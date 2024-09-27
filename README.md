# Javascript
Html
div>
    <form action="">
      <div>
        <label for="name">Item name</label>
        <input type="text" id="name" name="itemName" ng-model ="c.name" required/>
      </div>
      <div>
        <label for="description">Item description</label>
        <textarea name="" id="description" name="itemDesc" ng-model = "c.desc" required/></textarea>
      </div>
      <div>
        <label for="cost">Item Cost</label>
        <input type="number" id="cost" name="itemCost" ng-model = "c.cost" required/>
      </div>
      <div>
        <label for="image">Item image</label>
        <input type="file" id = "image" name="itemImage" ng-model = "c.image" required/>
      </div>
      <button ng-click = "c.submit()">Submit</button>
    </form>
  </div>

  client script:api.controller = function(){
	var c = this;
	c.sumbit = function(){}
	c.data.itemName = c.name;
	c.data.itemDesc = c.desc;
	c.data.itemCost = c.cost;
	c.data.itemImage = c.image;
	
}
server script:(function() {
  /* populate the 'data' object */
  /* e.g., data.table = $sp.getValue('table'); */
	if (input){
    var foodItem = new GlideRecord('x_snc_ice_garden_r_hotelportal');
    foodItem.initialize();
    foodItem.setvalue = ('itemname',input.itemName);
		foodItem.setvalue = ('itemdesc',input.itemDesc);
		foodItem.setvalue = ('itemcost',input.itemCost);
		foodItem.setvalue = ('itemimage',input.itemImage);
    foodItem.insert();
}
})();
