# Javascript
<div>
  <form>
    <div>
      <label for="name">Item Name</label>
      <input type="text" id="name" ng-model="c.item.name" required />
    </div>

    <div>
      <label for="description">Item Description</label>
      <textarea id="description" ng-model="c.item.description" required></textarea>
    </div>

    <div>
      <label for="cost">Item Cost</label>
      <input type="number" id="cost" ng-model="c.item.cost" required />
    </div>

    <div>
      <label for="image">Item Image</label>
      <input type="file" id="image" file-model="c.item.image" required />
    </div>

    <button type="button" ng-click="c.submit()">Submit</button>
  </form>

  <!-- Optionally, show a success or error message -->
  <div ng-if="c.successMessage">{{ c.successMessage }}</div>
  <div ng-if="c.errorMessage">{{ c.errorMessage }}</div>
</div>

CCS
api.controller = function($scope, $http, spModal) {
  var c = this;

  // Model to hold form data
  c.item = {
    name: '',
    description: '',
    cost: '',
    image: null // Handle image upload separately
  };

  // Function to handle form submission
  c.submit = function() {
    // Basic validation
    if (!c.item.name || !c.item.description || !c.item.cost || !c.item.image) {
      c.errorMessage = "All fields are required.";
      return;
    }

    // Send data to the server-side script
    c.data.itemName = c.item.name;
    c.data.itemDescription = c.item.description;
    c.data.itemCost = c.item.cost;
    c.data.itemImage = c.item.image; // Image handling could be more complex if actual file upload needed

    // Server call
    c.server.update().then(function(response) {
      if (response.success) {
        c.successMessage = "Item successfully added!";
        c.errorMessage = null;
      } else {
        c.errorMessage = "Error adding item.";
        c.successMessage = null;
      }
    }).catch(function(error) {
      c.errorMessage = "Error submitting form: " + error;
    });
  };
};

// For handling file input (ng-model doesn't bind to file input)
app.directive("fileModel", ['$parse', function($parse) {
  return {
    restrict: 'A',
    link: function(scope, element, attrs) {
      var model = $parse(attrs.fileModel);
      var modelSetter = model.assign;

      element.bind('change', function() {
        scope.$apply(function() {
          modelSetter(scope, element[0].files[0]);
        });
      });
    }
  };
}]);
sss
(function() {
  if (input) {
    var gr = new GlideRecord('x_your_custom_table'); // Replace with your table name
    gr.initialize();

    // Set values for the fields
    gr.setValue('item_name', input.itemName);       // Replace 'item_name' with your actual field name
    gr.setValue('item_description', input.itemDescription); // Replace with actual field name
    gr.setValue('item_cost', input.itemCost);       // Replace with actual field name

    // Handle file uploads (e.g., saving image)
    if (input.itemImage) {
      var attachmentSysId = gs.getProperty('glide.attachment.max_size', '5000'); // Add image as attachment
      var attachment = new GlideSysAttachment();
      attachment.write(gr, input.itemImage.name, input.itemImage.type, input.item

