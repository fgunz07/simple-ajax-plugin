### How to create ajax plgin ?

##### Create file name ajax.js
__import query.min.js__
```html
<script src="jquery.min.js"></script>
```

```javascript
	function ajax(Options) {
		return $.ajax({
			  url: Options.url,
			  method: Options.method,
			  data: Options.data
			})
			.always(() => {
			  //.. read this before other functions
			})
			.fail((err) => {
			  alert(error.message);
			})
	}
	
```

Now you have ajax file , you dont have to call $.ajax all the time all you need to do is use the __ajax__ function we have created.

### ```Hint: Best way separate ajax routes/url/uri```

#### Create config_api.urls.js

```javascript
	const users = {
		list: 'index.php',
		add : 'add.php',
		show: 'show.php',
		update: 'update.php',
		delete: 'delete.php'
	}
```

### Now in our html file lets import the files
import our __ajax.js__ and our __config_api.urls.js__

```html
<script src="ajax.js"></script>
<script src="config_api.js"></script>
```

### And our our index.html file

```html
<script src="jquery.min.js"></script>
<script src="ajax.js"></script>
<script src="config_api.js"></script>
<script type="text/javascript">
	//add a new user
	$('btn-add').on('click', function(){
		const options = {
			url: users.add,
			method: 'POST',
			data: { username: 'Sample', password: 'sample' }		
		};
		
		//call our ajax function and pass the options to be used on ajax request
		ajax(options)
		.done(function(response) {
			// do something for your response		
		});	
	});
	
	$('btn-list').on('click', function(){
		const options = {
			url: users.list,
			method: 'GET',
			data: {}		
		};
		
		//call our ajax function and pass the options to be used on ajax request
		ajax(options)
		.done(function(response) {
			// do something for your response		
		});	
	});

	$('btn-show').on('click', function(){
		const options = {
			url: users.show,
			method: 'GET',
			data: { user_id: '2' }		
		};
		
		//call our ajax function and pass the options to be used on ajax request
		ajax(options)
		.done(function(response) {
			// do something for your response		
		});	
	});

	$('btn-update').on('click', function(){
		const options = {
			url: users.update,
			method: 'PUT',
			data: { username: 'Sample', password: 'Sample'}		
		};
		
		//call our ajax function and pass the options to be used on ajax request
		ajax(options)
		.done(function(response) {
			// do something for your response		
		});	
	});

	$('btn-delete').on('click', function(){
		const options = {
			url: users.delete,
			method: 'DELETE',
			data: {user_id: '2' }		
		};
		
		//call our ajax function and pass the options to be used on ajax request
		ajax(options)
		.done(function(response) {
			// do something for your response		
		});	
	});
</script>
```

#### Congrats you have created your own ajax plugin


