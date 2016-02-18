# mapgeocodeangular
Dynamic Map using GeoCoder AngularJS

mapgeocodeangular package for interacting with:

- Google's Geocoding API


For Google GeoCoding

   var mapOptions = {
            center: new google.maps.LatLng(-34.397, 150.644),
            zoom: 16,
            mapTypeId: google.maps.MapTypeId.ROADMAP
        };
        map = new google.maps.Map(document.getElementById("map"),mapOptions);
           
        var geocoder = new google.maps.Geocoder();
        geocoder.geocode({ 'address': address }, function (results, status) {
		
            if (status == google.maps.GeocoderStatus.OK) {
                map.setCenter(results[0].geometry.location);
                var marker = new google.maps.Marker({
                    map: map,
                    position: results[0].geometry.location,
                    title: results[0].formatted_address
                });
                var infowindow = new google.maps.InfoWindow({ content: address });
                infowindow.open(map, marker);
                google.maps.event.addListener(marker, 'click', function () { infowindow.open(map, marker); });
            } 
			else{
                alert("Problem with geolocation");
			}
        });



