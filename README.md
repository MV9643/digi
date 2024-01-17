# digi
my dynamic digi clock
<html>
<head>
	<title>
		Digital Clock
	</title>
	<meta charset="UTF-8">
	<style>
		*
		{
			margin:0;
			padding:0;
			bos-sizing:border-box;
			font-family:'Anton',sans-serif;
		}
		body
		{
			display:flex;
			justify-content:center;
			align-items:center;
			min-height:100vh;
			background:gray;
		}
		.Clock
		{
			position:relative;
			display:flex;
			gap:20px;
		}
		.clock .Digital
		{
			position:relative;
			width:120px;
			height:120px;
			display:flex;
			justify-content:center;
			align-items:center;
			background:#c9d5e0;
			border-radius:30px;
			box-shadow:20px 20px 20px -10px rgba(0,0,0,0.15), inset 15px 15px 10px rgba(255,255,255,0.5),-15px -15px 35px rgba(255,255,255,0.35),inset -1px -1px 10px rgba(0,0,0,0.2);
		}
		.clock .digital .screen
		{
			position:absolute;
			inset:20px;
			background:#152b4a;
			border-radius:20px;
			display:flex;
			justify-content:center;
			align-items:center;
			box-shadow:5px 5px 15px 0px #152b4a66, inset 5px 5px 5px rgba(255,255,255,0.35),-6px -6px 10px rgba(255,255,255,1);
		}
		.clock .digital .screen::before
		{
			content:attr(data-text);
			position:absolute;
			bottom:-21px;
			left:50%;
			transform:translateX(-50%) scale(0.75);
			latter-spacing:0.1em;
			color:#333;
			text-transform:uppercase;
		}
		.clock .digital .time
		{
			position:absolute;
			inset:0;
			display:flex;
			justify-content:center;
			align-items:center;
		}
		.clock .digital .time div
		{
			position:relative;
			font-size:2.9em;
			color:var(color);
			letter-spacing:0.1em;
			margin-left:0.1em;
		}
		.clock .digital:nth-last-child(2) .time div
		{
			--color:transparent;
			-webkit-text-stroke:2px var(color);
		}
		.clock .digital:last-child::before
		{
			content:'';
			position:absolute;
			width:4px;
			height:4px;
			background:#152b4a;
			border:2px solid #fff;
			z-index:100000;
			border-radius:50%;
		}
		.clock .digital:last-child::after
		{
			content:'';
			position:absolute;
			inset:20px;
			background:#152b4a;
			border-radius:50%;
			box-shadow:5px 5px 15px 0px #152b4a66, inset 5px 5px 5px rgba(255,255,255,0.35),-6px -6px 10px rgba(255,255,255,1);
		}
		.box
		{
			position:absolute;
			inset:0;
			border-radius:50%;
			z-index:1000;
		}
		.box::after
		{
			content:'';
			position:absolute;
			left:50%;
			bottom:50%;
			transform:translateX(-50%);
			width:2px;
			height:30px;
			background:var(color);
			border-radius:4px;
		}
		.box:nth-child(1):after
		{
			height:20px;
			width:4px;
		}
		.box:nth-child(2):after
		{
			height:25px;
			width:3px;
		}
		#ampm
		{
			position:absolute;
			bottom:0;
			left:50%;
			transform:translateX(-50%) scale(0.75);
			color:#333;
			latter-spacing:0.1em;
		}
	</style>
</head>
<body>
	<div class="clock">
		<div class="digital" style="color:red">
			<div class="screen" data-text="Hours">
				<div class="time">
					<div id="hour"></div>
				</div>
			</div>
		</div>
		<div class="digital" style="color:blue">
			<div class="screen" data-text="Minutes">
				<div class="time">
					<div id="minute"></div>
				</div>
			</div>
		</div>
		<div class="digital" style="color:green">
			<div class="screen" data-text="Seconds">
				<div class="time">
					<div id="second"></div>
				</div>
			</div>
		</div>
		<div class="digital">
			<div class="box" id="hr" style="color:red"></div>
			<div class="box" id="hr" style="color:blue"></div>
			<div class="box" id="hr" style="color:green"></div>
			<div id="ampm"></div>
		</div>
	</div>
	<script>
		let hour = document.getElementById('hour');
		let minute = document.getElementById('minute');
		let second = document.getElementById('second');
		let ampm = document.getElementById('ampm');
		
		setInterval(() =>{
		let h = new Date().getHours();
		let m = new Date().getMinutes();
		let s = new Date().getSeconds();
		var am = h >= 12 ? 'PM' : 'AM';
		
		if (h > 12)
		{
			h = h - 12;
		}
		
		h = (h < 10) ? "0" + h : h
		m = (m < 10) ? "0" + m : m
		s = (s < 10) ? "0" + s : s
		
		hour.innerHTML = h;
		minute.innerHTML = m;
		second.innerHTML = s;
		ampm.innerHTML = am;
		})
	</script>
</body>
</html>
