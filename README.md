<!DOCTYPE html>
<html>
	<head>
		<style>
			body{
				background-color: black;
				overflow: hidden;
				width: 100%;
				height: 1000px;
			}
			#block{
				position: absolute;
				left: 50%;
				width: 300px;
				height: 100%;
				animation: beat 1.3s infinite;
			}
			#block::after{
				transform: translateX(-50%);
				width: 100%;
				height: 100%;
				position: absolute;
				
			}
			.mySpan{
				position: absolute;
				pointer-events: none;
				filter: drop-shadow(0 0 15px rgba(0, 0, 0, 0.5));
				animation: fadeOut 1s infinite;
			}
			.mySpan::before{
				content: '';
				position: absolute;
				width: 100%;
				height: 100%;
				background: url('heart.png');
				background-size: cover;
				animation: moveHeart 1s infinite;
			}
			.newspan{
				position: absolute;
				pointer-events: none;
				width: 30px;
				height: 30px;
				
				animation: fadeOut 1s infinite;
			}
			.newspan::before{
				content: '';
				position: absolute;
				width: 100%;
				height: 100%;
				background: url('heart.png');
				background-size: cover;
				animation: moveHeart2 1s infinite;
			}
			#text{
				position: absolute;
				top: 50%;
				left: 50%;
				color: hotpink;
				animation: beat 1.3s infinite;
			}
			@keyframes moveHeart{
				0%{
					transform: translate(0px) rotate(0deg);
				}
				100%{
					transform: translate(300px) rotate(360deg);
				}
			}
			@keyframes fadeOut{
				0%,100%{
					opacity: 30%;
				}
				20%,40%,60%,80%{
					opacity: 100%;
				}
			}
			@keyframes moveHeart2{
				0%{
					transform: translate(10px) scale(0);
					opacity: 30%;
				}
				30%{
					transform: translate(20px) scale(10px);
					opacity: 100%;
				}
				60%{
					transform: translate(30px) scale(20px);
					opacity: 100%;
				}
				100%{
					transform: translate(500%);
				}
				
			}
			@keyframes beat{
				0% {
					transform: scale(1) translate(-50%);
				}
				30% {
					transform: scale(0.8) translate(-50%);
				}
				60% {
					transform: scale(1.2) translate(-50%);
				}
				100% {
					transform: scale(1) translate(-50%);
				}
			}
		</style>
	</head>
	<body id="body">
		<div id="block"></div>
		<div id="text">VIASANA</div>
		
	</body>
	<script>
		document.addEventListener('mousemove', function(e){
			let body = document.getElementById('body');
			let heart = document.createElement('span');
			let x = e.offsetX;
			let y = e.offsetY;

			heart.style.left = x +'px';
			heart.style.top = y + 'px';

			heart.className = 'mySpan';

			let size = Math.random() *80;
			heart.style.width = 20 + size + 'px';
			heart.style.height = 20 + size + 'px';

			let tranform = Math.random() *80;
			heart.style.transform = 'rotate('+ tranform +'deg)';

			body.appendChild(heart);

			setTimeout(function(){
				heart.remove();
			}, 1000);
		})
		setInterval(function(){
			let body = document.getElementById('block');
			let heart = document.createElement('span');
			let delta

			alpha = Math.random() * 360;

			heart.className = 'newspan';
			heart.style.top = '50%';
			heart.style.left = '50%';
			heart.style.transform = 'rotate('+ alpha +'deg)';
			body.appendChild(heart);
			setTimeout(function(){
				heart.remove();
			}, 1000);
		}, 1)
	</script>
</html>
