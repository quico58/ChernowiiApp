ChernowiiApp
============
<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Transitional//EN" "http://www.w3.org/TR/xhtml1/DTD/xhtml1-transitional.dtd">
<html xmlns="http://www.w3.org/1999/xhtml">
<head>
<meta http-equiv="Content-Type" content="text/html; charset=UTF-8" />
<title>WiFiController</title>
<style type="text/css">
body {
  background-image: url(fondo.png);
	background-repeat: repeat-y;
}
</style>
</head>
<html>
	<head>
		<title>GoPro WiFi bacpac WEB App</title>
		<script type='text/JavaScript'>
			function getXhr(){
				var xhr = null;
				if(window.XMLHttpRequest) // Firefox et autres
					xhr = new XMLHttpRequest();
				else if(window.ActiveXObject){ // Internet Explorer
					try {
						xhr = new ActiveXObject("Msxml2.XMLHTTP");
					} catch (e) {
						xhr = new ActiveXObject("Microsoft.XMLHTTP");
					}
				}
				else { // XMLHttpRequest non support� par le navigateur
					alert("Votre navigateur ne supporte pas les objets XMLHTTPRequest...");
					xhr = false;
				}
				return xhr
			}
			
			/**
			* Command
			*/
			function command(device, app, command){
				var xhr = getXhr()
				// On d�fini ce qu'on va faire quand on aura la r�ponse
				xhr.onreadystatechange = function(){
					// On ne fait quelque chose que si on a tout re�u et que le serveur est ok
					if(xhr.readyState == 4 && xhr.status == 200){
						alert(xhr.responseText);
					}
				}
				xhr.open('GET','http://10.5.5.9:80/'+device+'/'+app+'?t='+document.getElementById('wifiPassword').value+'&p='+command);
				xhr.send(null);
			}
		</script>
		<meta http-equiv="Content-Type" content="text/html; charset=UTF-8" />
</head>
	<body>
		<table border=1 cellpadding=3 cellspacing=0>
		<tr>
		  <td colspan=2>&nbsp;</td>
	</tr>
			<tr>
				<td colspan=2>
					<p>GoPro WiFI Controller<br/><br/>
                    Type your WiFi Password : <input id="wifiPassword" type="text"/> 
</p>
					<p>
					  <button onclick="command('bacpac','PW','%01')">Turn GoPro ON</button>
				  </p>
				  <p><br/>
					  <button onclick="command('bacpac','SH','%01')">Fire!</button> <button onclick="command('bacpac','SH','%00')">Stop </button>
				  </p>
					<p>
					  <button onclick="command('bacpac','PW','%00')">
				      <p>Turn GoPro OFF</p>
  </button>
				  </p>
					<p>Modes:</p>
				  <p>
                    <button onclick="command('camera','CM','%00')">Video</button>
					<button onclick="command('camera','CM','%01')">Photo</button>
					<button onclick="command('camera','CM','%02')">Burst</button>
					<button onclick="command('camera','CM','%03')">Timelapse</button>
					<button onclick="command('camera','CM','%04')">Timer</button>&nbsp; </p>
					<p>Nuts and bolts:</p>
				  <p>Orientation:</p>
					<p>
                    <button onclick="command('camera','UP','%00')">Up</button>
					<button onclick="command('camera','UP','%01')">Down</button>&nbsp;</p>
				  <p>Video Resolution:</p>
					<p>
                    <button onclick="command('camera','VR','%00')">WVGA-60</button>
					<button onclick="command('camera','VR','%01')">WVGA-120</button>
					<button onclick="command('camera','VR','%02')">720-30</button>
					<button onclick="command('camera','VR','%03')">720-60</button>
					<button onclick="command('camera','VR','%04')">960-30</button>
					<button onclick="command('camera','VR','%05')">960-40</button>
					<button onclick="command('camera','VR','%06')">1080-30</button>
					</p>
					<p>FOV:</p>
					<p>
                    <button onclick="command('camera','FV','%00')">wide</button>
					<button onclick="command('camera','FV','%01')">medium</button>
					<button onclick="command('camera','FV','%02')">narrow</button>&nbsp; </p>
					<p>Photo Definition:</p>
				  <p>
                    <button onclick="command('camera','PR','%00')">11mp wide</button>
					<button onclick="command('camera','PR','%01')">8mp medium</button>
					<button onclick="command('camera','PR','%02')">5mp wide</button>
					<button onclick="command('camera','PR','%03')">5mp medium</button>&nbsp;</p>
					<p>Timelapse Interval:</p>
					<p>
                    <button onclick="command('camera','TI','%00')">0,5sec</button>
					<button onclick="command('camera','TI','%01')">1sec</button>
					<button onclick="command('camera','TI','%02')">2sec</button>
					<button onclick="command('camera','TI','%05')">5sec</button>
					<button onclick="command('camera','TI','%0a')">10sec</button>
					<button onclick="command('camera','TI','%1e')">30sec</button>
					<button onclick="command('camera','TI','%3c')">60sec</button>&nbsp;</p>
					<p>Volume:</p>
					<p>
                    <button onclick="command('camera','BS','%00')">0%</button>
					<button onclick="command('camera','BS','%01')">70%</button>
					<button onclick="command('camera','BS','%02')">100%</button>&nbsp;</p>
                    <p>Delete(Black Ed Only):</p>
                  <button onclick="command('camera','DL')">Delete Last File</button>&nbsp;</p>
                    <button onclick="command('camera','DA')">Delete All </button>
                    <p>Photo Resolution(Black Ed):</p>
                    <button onclick="command('camera','PR','%05')">12mpW</button>
<button onclick="command('camera','PR','%04')">7mpW</button>
<button onclick="command('camera','PR','%06')">7mpM</button>
<button onclick="command('camera','PR','%03')">5mpM</button>

					<p>Leds: </p>
                    <button onclick="command('bacpac','LB','%00')">No leds</button>
<button onclick="command('camera','LB','%01')">2 leds</button>
<button onclick="command('camera','LB','%02')">4 leds</button>
<p>Spot Meter: </p>
<button onclick="command('camera','EX','%00')">OFF</button>
<button onclick="command('camera','EX','%01')">ON</button>
<p>One Button mode: </p>
<button onclick="command('camera','OB','%00')">OFF</button>
<button onclick="command('camera','OB','%01')">ON</button>

<p>Protune Mode:</p>
<button onclick="command('camera','PT','%00')">OFF</button>
<button onclick="command('camera','PT','%01')">ON</button>
<p>Auto power off:</p>
<button onclick="command('camera','AO','%00')">NEVER</button>
<button onclick="command('camera','AO','%01')">60s</button>
<button onclick="command('camera','AO','%02')">120s</button>
<button onclick="command('camera','AO','%03')">300s</button>
<p>Default Mode:</p>
<button onclick="command('camera','DM','%00')">Video</button>
<button onclick="command('camera','DM','%01')">Photo</button>
<button onclick="command('camera','DM','%02')">Burst</button>
<button onclick="command('camera','DM','%03')">Timelapse</button>
<p>OnScreen Display:</p>
<button onclick="command('camera','OS','%00')">OFF</button>
<button onclick="command('camera','OS','%01')">ON</button>


<p>Thanks to tavarn.org (dough29)
                    </p>
					<p><br/>					
				  </p>
              </body>
</html>
