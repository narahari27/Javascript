<div class="field-container">
    <label for="">Item name</label><br>
    <input type="text" name="Name" ng-model ="c.name"><br>
    <label for="">Item Description</label><br>
    <textarea name="desc" id="" placeholder="Description for Dish" ng-model="c.desc"></textarea><br>
    <label for="">Item Cost</label>
    <input type="number" name="cost" ng-model="c.cost"><br>
    <div class="btn-class">
      <button type="buton" ng-click ="c.submit()">Submit</button>
    </div>
   </div>
   api.controller = function($scope){
	var c = this;
	c.submit = function(){
		c.data.Name = c.name;
		c.data.desc = c.desc;
		c.data.cost = c.cost;
		c.server.update();
		console.log();
	}
}
(function() {
  /* populate the 'data' object */
  /* e.g., data.table = $sp.getValue('table'); */
	if (input){
    var gr = new GlideRecord("x_snc_ice_garden_r_hotelportal");
    gr.initialize();
    gr.setValue = ('itemname',input.Name);
		gr.setValue = ('itemdesc',input.desc);
		gr.setValue = ('itemcost',input.cost);
		
    gr.insert();
		console.log();
}
})();

http://www.john-james-andersen.com/blog/service-now/post-picture-image-field-rest.html
