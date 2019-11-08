<!DOCTYPE html>
<html lang="en" dir="ltr">
<head>
	<meta charset = "utf-8">
	<title>Google maps API use</title>
	<script src="https://ajax.googleapis.com/ajax/libs/jquery/3.4.1/jquery.min.js"></script>
</head>
<body>
	<div style="padding:10px;">
	Search <input type="text" id="search" placeholder="Enter Location">
	<button type="button" onclick="myFunction()">Submit</button>
	</div>
	<iframe id = "frame1"
	  frameborder="0" style="border:0"
	  style="position:fixed; top:0; left:0; bottom:0; right:0; margin:0; padding:0;"
	  height="500"
	  width="1200"
	  src="https://www.google.com/maps/embed/v1/place?key=AIzaSyDNRmufQHfCRrlCbsx_n_VNoSSploKRB2c
	    &q=Holden+Hall" allowfullscreen>
	</iframe>
	<iframe id = "frame2"
	  frameborder="0" style="border:0"
	  style="position:fixed; top:0; left:0; bottom:0; right:0; margin:0; padding:0;"
	  height="500"
	  width="200"
	  src="https://api.openweathermap.org/data/2.5/weather?q=London&mode=html&APPID=d9dca2d4ffaa960fcb0da6f0f6e00115" allowfullscreen>
	</iframe>
	
	<script>
		function myFunction() {
			var x = document.getElementById("search").value; 
			document.getElementById("frame1").src = "https://www.google.com/maps/embed/v1/place?key=AIzaSyDNRmufQHfCRrlCbsx_n_VNoSSploKRB2c&q="+x.replace(" ","+");
			$.getJSON("https://api.opencagedata.com/geocode/v1/geojson?q=" + x.replace(" ","+") + "&key=0a271cf946a0439180ba806ebadf4a91", function(result){
				document.getElementById("frame2").src = "https://api.openweathermap.org/data/2.5/weather?lat=" + parseFloat(result.features[0].geometry.coordinates[1]).toPrecision(4) + "&lon=" + parseFloat(result.features[0].geometry.coordinates[0]).toPrecision(4) + "&mode=html&APPID=d9dca2d4ffaa960fcb0da6f0f6e00115";
		    });  
		}
	</script>
</body>
</html>
