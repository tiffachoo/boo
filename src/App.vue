<template>
	<div id="app">
		<div class="pattern-wrapper">
			<svg class="pattern-bg" id="castle" viewBox="0 0 500 500">
				<defs>
					<pattern id="castleBrick" width="62" height="70" patternUnits="userSpaceOnUse" viewBox="0 0 115 130">
						<rect class="no-fill-for-you" width="115" height="130"/>
						<rect class="castle-fill" width="100" height="50" rx="15" ry="15"/>
						<path class="castle-fill" d="M27.5,65H0v50H27.5a15,15,0,0,0,15-15V80A15,15,0,0,0,27.5,65Z"/>
						<path class="castle-fill" d="M115,65H72.5a15,15,0,0,0-15,15v20a15,15,0,0,0,15,15H115Z"/>
					</pattern>
				</defs>
				<rect class="castle-pattern" width="500" height="500"/>
			</svg>
		</div>
		
		<svg 
			id="boo" 
			ref="boo"
			viewBox="0 0 150 150"
		>
			<defs>
				<clipPath id="clipMouth">
					<path class="no-fill-for-you" d="M64.13,73.09C60.7,75.27,49,79.25,39.4,79.43A33.12,33.12,0,0,1,24.68,76.1s5.82,34.29,20.7,34.29C64.13,110.4,64.13,73.09,64.13,73.09Z"/>
				</clipPath>
			</defs>
			<title>boo</title>
			<g 
				:class="{ mirror: onRight, cover: !movingAway }"
				class="inner-wrapper" 
			>
				<g id="armLeft">
					<g v-if="movingAway">
						<path class="boo-body-fill" d="M15.94,82.21s-15.1-21.7-7.69-29c2.07-2,19.51,6.32,20.55,21.55a26.51,26.51,0,0,1-2.19,12.38c-4,9.31-4,8.36-4,8.36L20,87.05Z"/>
						<path class="boo-body-stroke" d="M18.94,83.21s-15.1-21.7-7.69-29c2.07-2,19.51,6.32,20.55,21.55,1.13,16.63-4.91,23-4.91,23"/>
					</g>
				</g>
				<g id="body">
					<path class="boo-shadow-fill" d="M140.47,81c-1.32-1.56-5.05-.27-9.38.62a19.65,19.65,0,0,1-2.91.36c0-.61,0-1.22,0-1.84a53.46,53.46,0,1,0-53.46,53.46q1.36,0,2.7-.07h0c36.39,0,53.72-28.41,58-34.56S142.18,83,140.47,81Z"/>
					<path class="boo-body-fill" d="M134.47,70c-1.32-1.56-5.05-.27-9.38.62a19.65,19.65,0,0,1-2.91.36c0-.61,0-1.22,0-1.84a53.46,53.46,0,1,0-53.46,53.46q1.36,0,2.7-.07h0c36.39,0,53.72-28.41,58-34.56S136.18,72,134.47,70Z"/>
					<path class="boo-body-stroke" d="M136.47,74c-1.32-1.56-5.05-.27-9.38.62a19.65,19.65,0,0,1-2.91.36c0-.61,0-1.22,0-1.84a53.46,53.46,0,1,0-53.46,53.46q1.36,0,2.7-.07h0c36.39,0,53.72-28.41,58-34.56S138.18,76,136.47,74Z"/>
					<g id="pinky">
						<ellipse class="boo-pink-fill pink-3" cx="51.394" cy="79.598" rx="28.784" ry="24.861"/>
						<ellipse class="boo-pink-fill pink-2" cx="47.394" cy="79.598" rx="20.243" ry="17.484"/>
						<ellipse class="boo-pink-fill pink-1" cx="43.394" cy="79.598" rx="9.963" ry="8.605"/>
					</g>
				</g>
				<g id="armRight">
					<path class="boo-body-fill" d="M92.37,85.84S114.71,63.64,108.91,55c-4.15-6.2-31.38,11.48-31.38,11.48"/>
					<path class="boo-body-stroke" d="M94.37,81.84S116.71,59.64,110.91,51c-4.15-6.2-31.38,11.48-31.38,11.48"/>
				</g>
				<g id="eyeRight">
					<g class="boo-eye">
						<path class="boo-stroke-fill" d="M48.92,59.92c0,4.29-.3,7.77-3.23,7.77s-3.23-3.48-3.23-7.77,1.45-7.77,3.23-7.77S48.92,55.63,48.92,59.92Z"/>
						<path class="boo-highlight-fill" d="M46.8,58.73c0,2.06-.13,3.74-1.41,3.74S44,60.79,44,58.73,44.61,55,45.39,55,46.8,56.66,46.8,58.73Z"/>
					</g>
					<path 
						class="boo-eyelid boo-inner-stroke boo-highlight-fill" 
						d="M60.61,47.1c-1.86,5.31-7,9.64-13.08,9.39a11.14,11.14,0,0,1-11-10.82"
					/>
					<transition name="fade-y">
						<path 
							v-if="!movingAway"
							class="boo-eyelid boo-body-stroke" 
							d="M48.55,83.83A25.36,25.36,0,0,1,62.8,79.1c6.86,0,10,2.71,10,2.71"
						/>
					</transition>
				</g>
				<g id="eyeLeft">
					<g class="boo-eye">
						<path class="boo-stroke-fill" d="M31.22,60.51c0,3.51-.24,6.36-2.64,6.36S25.93,64,25.93,60.51s1.18-6.36,2.64-6.36S31.22,57,31.22,60.51Z"/>
						<path class="boo-highlight-fill" d="M29.48,59.56c0,1.69-.11,3.06-1.16,3.06s-1.16-1.37-1.16-3.06.52-3.06,1.16-3.06S29.48,57.87,29.48,59.56Z"/>
					</g>
					<path 
						class="boo-eyelid boo-inner-stroke boo-highlight-fill" 
						d="M24.72,48.63c-1.48,6.57,1.31,7.66,4.63,7.66s7-4.84,7.15-10.62"
					/>
					<transition name="fade-y">
						<path 
							v-if="!movingAway"
							class="boo-eyelid boo-body-stroke" 
							d="M35.52,81.82s-5.08-5.34-9.61-5.57-5.25.87-5.25.87"
						/>
					</transition>
				</g>
				<g id="mouth">
					<g id="mouthOpen">
						<path class="boo-pink-fill-dark" d="M65.13,75.09C61.7,77.27,50,81.25,40.4,81.43A33.12,33.12,0,0,1,25.68,78.1s5.82,34.29,20.7,34.29C65.13,112.4,65.13,75.09,65.13,75.09Z"/>
						<g class="boo-mouth" style="clip-path: url(#clipMouth)">
							<ellipse class="boo-pink-fill" cx="63.14" cy="103.41" rx="21.86" ry="17.58"/>
							<ellipse class="boo-inner-stroke" cx="60.14" cy="102.41" rx="21.86" ry="17.58"/>
							<g>
								<g>
									<path class="boo-highlight-fill" d="M27.46,76s.71,13,6.09,16.74c3.23-7.25,2-16.74,2-16.74Z"/>
									<path class="boo-highlight-fill" d="M60.78,76s-.73,10.31-5.43,16.74C50.79,86.11,50.22,76,50.22,76Z"/>
									<path class="boo-highlight-fill" d="M35.31,76s1.35,10.29,5.17,13.62C43.23,83.76,42.19,76,42.19,76Z"/>
									<path class="boo-highlight-fill" d="M51.14,76s-1.06,9.25-5.58,13.62C42.22,83.76,42.75,76,42.75,76Z"/>
								</g>
								<g>
									<path class="boo-inner-stroke" d="M26.46,75s.71,13,6.09,16.74c3.23-7.25,2-16.74,2-16.74Z"/>
									<path class="boo-inner-stroke" d="M59.78,75s-.73,10.31-5.43,16.74C49.79,85.11,49.22,75,49.22,75Z"/>
									<path class="boo-inner-stroke" d="M34.31,75s1.35,10.29,5.17,13.62C42.23,82.76,41.19,75,41.19,75Z"/>
									<path class="boo-inner-stroke" d="M50.14,75s-1.06,9.25-5.58,13.62C41.22,82.76,41.75,75,41.75,75Z"/>
								</g>
							</g>
						</g>
						<path class="boo-inner-stroke" d="M64.13,73.09C60.7,75.27,49,79.25,39.4,79.43A33.12,33.12,0,0,1,24.68,76.1s5.82,34.29,20.7,34.29C64.13,110.4,64.13,73.09,64.13,73.09Z"/>
					</g>
					<path 
						id="mouthClosed" 
						class="boo-mouth-closed boo-inner-stroke" 
						:d="movingAway ? 'M22.64,75A32.84,32.84,0,0,0,39.4,79.43c9.56-.18,21.31-4.16,24.74-6.34' : 'M38.41,103.33s1.26-3.15,4-3.26,5.69,2,9.26,4.34'"
					/>
				</g>
				<g 
					v-if="!movingAway"
					id="armLeftFront" 
				>
					<path class="boo-body-fill" d="M28.12,82.21s15.1-21.7,7.69-29c-2.07-2-19.51,6.32-20.55,21.55a26.51,26.51,0,0,0,2.19,12.38,38.34,38.34,0,0,0,12,14.81L24,87.05Z"/>
					<path class="boo-body-stroke" d="M25.12,83.21s15.1-21.7,7.69-29c-2.07-2-19.51,6.32-20.55,21.55-1.13,16.63,14.15,27.19,14.15,27.19"/>
				</g>
			</g>
		</svg>
	</div>
</template>

<script>
import anime from 'animejs/lib/anime.es.js';

export default {
	name: 'App',
	data() {
		return {
			onRight: false,
			movingAway: true,
			booPos: '',
			mouseFromBooPos: 0,
			lastMouseFromBooPos: 0,
			appCenter: {
				x: 0,
				y: 0
			},
			throttle: false
		}
	},
	computed: {
		getCenter() {
			return this.booPos.left + (this.booPos.width / 2);
		},
		getDelta() {
			return Math.abs(this.lastMouseFromBooPos - this.mouseFromBooPos);
		}
	},
	mounted() {
		this.appCenter.x = window.innerWidth / 2;
		this.appCenter.y = window.innerHeight / 2;

		document.body.addEventListener('mousemove', this.getMousePos);
		
		anime({
			targets: '.boo-shadow-fill',
			translateY: -17,
			elasticity: 0,
			easing: 'linear',
			direction: 'alternate',
			loop: true,
			duration: 5000
		});
	},
	methods: {
		getMousePos(e) {
			if (!this.throttle) {
				this.throttle = true; 
				setTimeout(() => {
					const mousePos = { x: e.clientX, y: e.clientY };
					
					// move boo
					this.movingAway && document.documentElement.style.setProperty('--pos-x', -(this.appCenter.x - mousePos.x));
					this.movingAway && document.documentElement.style.setProperty('--pos-y', -(this.appCenter.y - mousePos.y));
					
					this.booPos = this.$refs.boo.getBoundingClientRect();
					this.mouseFromBooPos = this.getCenter - mousePos.x;
					
					// check where the mouse is relative to boo
					this.onRight = (this.mouseFromBooPos <= 0);
					if (this.getDelta > 15) {
						this.movingAway = ((!this.onRight && this.mouseFromBooPos > this.lastMouseFromBooPos) || (this.onRight && this.mouseFromBooPos < this.lastMouseFromBooPos));
					}
					
					if (!this.movingAway) {
						this.moveArm('#armRight', 180, 10);
						this.moveEye('#eyeRight');
						this.moveEye('#eyeLeft');
						this.moveMouth('#mouth', 'M38.41,103.33s1.26-3.15,4-3.26,5.69,2,9.26,4.34');
					} else {
						this.moveArm('#armRight', 0, 0);
						this.moveEye('#eyeRight', 1);
						this.moveEye('#eyeLeft', 1);
						this.moveMouth('#mouth', 'M22.64,75A32.84,32.84,0,0,0,39.4,79.43c9.56-.18,21.31-4.16,24.74-6.34', 1);
					}
					
					this.lastMouseFromBooPos = this.mouseFromBooPos;
					this.throttle = false;
				}, 100);
			}
		},
		moveArm(el, degY, deg) {
			let arm = anime({
				targets: el,
				rotateY: `${degY}deg`,
				rotate: `${deg}deg`,
				easing: 'linear',
				elasticity: 0,
				duration: 100
			});
			
			return arm;
		},
		moveEye(el, val = 0) {
			let eye = anime.timeline();
			eye 
				.add({
					targets: `${el} .boo-eye`,
					scaleY: val,
					easing: 'linear',
					elasticity: 0,
					duration: 100
				})
				.add({
					targets: `${el} .boo-eye`,
					opacity: val,
					easing: 'linear',
					elasticity: 0,
					duration: 0
				})
				.add({
					targets: `${el} .boo-inner-stroke.boo-eyelid`,
					opacity: val,
					easing: 'linear',
					elasticity: 0,
					duration: 1
				});
			
			return eye;
		},
		moveMouth(el, path, val = 0) {
			let mouth = anime.timeline();
			mouth
				.add({
					targets: `${el} #mouthOpen`,
					scaleY: val,
					easing: 'linear',
					elasticity: 0,
					duration: 100
				})
				.add({
					targets: `${el} #mouthOpen`,
					opacity: val,
					easing: 'linear',
					elasticity: 0,
					duration: 0
				})
				.add({
					targets: `${el} #mouthClosed`,
					// d: path,
					strokeWidth: val ? 1 : 2,
					easing: 'linear',
					elasticity: 0,
					duration: 200
				});
			
			return mouth;
		}
	}
}
</script>

<style lang="scss">
@import '@/styles/reset';
@import '@/styles/styles';
</style>
