//HTML
<div class="field-container">
    <label for="">Item name</label><br>
    <input type="text" name="Name" ng-model="c.name"><br>
    <label for="">Item Description</label><br>
    <textarea name="desc" id="" placeholder="Description for Dish" ng-model="c.desc"></textarea><br>
    <label for="">Item Cost</label><br>
    <input type="number" name="cost" ng-model="c.cost"><br>
    <label for="">Item Image</label><br>
    <input type="file" id="image" name="itemImage" ng-file-select onchange="angular.element(this).scope().c.handleFileSelect(this.files)"><br>
    <div class="btn-class">
        <button type="button" ng-click="c.submit()">Submit</button>
    </div>
</div>
//cLIENTScript
api.controller = function($scope, $window) {
    var c = this;

    
    c.imageBase64 = '';

    // To handle the file selection
    c.handleFileSelect = function(files) {
        var file = files[0]; 

        if (file) {
            var reader = new FileReader();

            reader.onloadend = function() {
                c.imageBase64 = reader.result;
                $scope.$apply(); 
            };

            reader.readAsDataURL(file); 
        } else {
            console.log("No file selected or an error occurred");
        }
    };

    // To submit the form data
    c.submit = function() {
        c.data.name = c.name;
        c.data.desc = c.desc;
        c.data.cost = c.cost;
        if (c.imageBase64) {
        c.data.image = c.imageBase64;  
    }

        
        c.server.update().then(function() {
            console.log("Data submitted successfully");
            $window.location.href = '/garden_restaurant?id=food_itemspage';
        }).catch(function(error) {
            console.error("Error submitting data:", error);
        });
    };
};
//Server side script

(function() {
  if (input) {
    var gr = new GlideRecord('x_snc_ice_garden_r_hotel_portal'); 
    gr.initialize();

    
    gr.setValue('itemname', input.name);
    gr.setValue('itemdesc', input.desc);
    gr.setValue('itemcost', input.cost);

    
    if (input.imageBase64) {
      gr.setValue('itemimageone', input.image); 
    }

    var newRecordID = gr.insert();

    
    if (newRecordID) {
      data.newRecordID = newRecordID; 
    } else {
      data.error = 'Failed to insert record'; 
    }
		c.server.update().then(function(response) {
    console.log(response);  
});
  }
})();
