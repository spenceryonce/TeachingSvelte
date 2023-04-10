<script lang="ts">
	import { onMount, onDestroy } from 'svelte';
	import * as THREE from 'three';

	let age = 37.5;
	let renderer: THREE.WebGLRenderer;

	onMount(() => {
		const scene = new THREE.Scene();
		const camera = new THREE.PerspectiveCamera(
			75,
			window.innerWidth / window.innerHeight,
			0.1,
			1000
		);

		renderer = new THREE.WebGLRenderer() as THREE.WebGLRenderer;
		renderer.setSize((window.innerWidth / 10) * 5, (window.innerHeight / 10) * 5);
		document.getElementById('three-container')?.appendChild(renderer.domElement);

		// Define some colors
		const ambientLight = new THREE.AmbientLight(0xffffff, 1.0);
		const directionalLight = new THREE.DirectionalLight(0xffffff, 1.0);
		directionalLight.position.set(1, 1, 1);
		scene.add(ambientLight, directionalLight);

		// Define some colors
		const colors = {
			white: 0xffffff,
			black: 0x000000,
			gray: 0x808080,
			red: 0xff0000,
			green: 0x00ff00,
			blue: 0x0000ff,
			tan: 0xf5deb3
		};

		// Create the head
		const headGeometry = new THREE.SphereGeometry(1, 16, 16);
		const headMaterial = new THREE.MeshStandardMaterial({ color: colors.white });
		const head = new THREE.Mesh(headGeometry, headMaterial);
		head.position.set(0, 3, 0);
		scene.add(head);

		// Create the body
		const bodyGeometry = new THREE.BoxGeometry(1, 2, 0.5);
		const bodyMaterial = new THREE.MeshStandardMaterial({ color: colors.gray });
		const body = new THREE.Mesh(bodyGeometry, bodyMaterial);
		body.position.set(0, 1, 0);
		scene.add(body);

		// Create the arms
		const armGeometry = new THREE.BoxGeometry(0.5, 1, 0.5);
		const armMaterial = new THREE.MeshStandardMaterial({ color: colors.red });
		const leftArm = new THREE.Mesh(armGeometry, armMaterial);
		leftArm.position.set(-1, 1, 0);
		scene.add(leftArm);

		const rightArm = new THREE.Mesh(armGeometry, armMaterial);
		rightArm.position.set(1, 1, 0);
		scene.add(rightArm);

		// Create the legs
		const legGeometry = new THREE.BoxGeometry(0.5, 1.5, 0.5);
		const legMaterial = new THREE.MeshStandardMaterial({ color: colors.green });
		const leftLeg = new THREE.Mesh(legGeometry, legMaterial);
		leftLeg.position.set(-0.5, -1, 0);
		scene.add(leftLeg);

		const rightLeg = new THREE.Mesh(legGeometry, legMaterial);
		rightLeg.position.set(0.5, -1, 0);
		scene.add(rightLeg);

		// Create the floor
		const floorGeometry = new THREE.PlaneGeometry(10, 10);
		const floorMaterial = new THREE.MeshStandardMaterial({ color: colors.green });
		const floor = new THREE.Mesh(floorGeometry, floorMaterial);
		floor.rotation.x = -Math.PI / 2;
		floor.position.set(0, -1.5, 0);
		scene.add(floor);

		// Create the walls
		const wallGeometry = new THREE.BoxGeometry(10, 5, 0.2);
		const wallMaterial = new THREE.MeshStandardMaterial({ color: colors.tan });
		const backWall = new THREE.Mesh(wallGeometry, wallMaterial);
		backWall.position.set(0, 2.5, -5);
		scene.add(backWall);

		// Wall on the left side of the scene
		const leftWall = new THREE.Mesh(wallGeometry, wallMaterial);
		leftWall.rotation.y = Math.PI / 2;
		leftWall.position.set(-5, 2.5, 0);
		scene.add(leftWall);

		// Wall on the right side of the scene
		const rightWall = new THREE.Mesh(wallGeometry, wallMaterial);
		rightWall.rotation.y = -Math.PI / 2;
		rightWall.position.set(5, 2.5, 0);
		scene.add(rightWall);

		// Position the camera
		camera.position.z = 10;
		camera.position.y = 3;

		// Create an animation loop
		function animate() {
			requestAnimationFrame(animate);

			head.rotation.x += 0.01;
			head.rotation.y += 0.01;

			leftArm.rotation.x += 0.02;
			rightArm.rotation.x -= 0.02;

			leftLeg.rotation.x -= 0.02;
			rightLeg.rotation.x += 0.02;

			renderer.render(scene, camera);
		}
		// Start the animation loop
		animate();
	});
	onDestroy(() => {
		renderer.dispose();
		//remove dom element
		renderer.domElement.remove();
	});
</script>

<main class="container">
	<h1>Create Character!</h1>

	<form>
		<div class="container">
			<label for="charactername">
				Character Name
				<input
					type="text"
					id="charactername"
					name="charactername"
					placeholder="Character name"
					required
				/>
			</label>

			<!-- Select -->
			<label for="gender">Gender</label>
			<select id="gender" required>
				<option value="" selected>Select a gender...</option>
				<option value="male">Male</option>
				<option value="female">Female</option>
			</select>

			<!-- Range slider -->
			<label for="age"
				>Choose your character's Age
				<input type="range" min="5" max="80" bind:value={age} id="age" name="age" />
			</label>
			<p>Age: {age}</p>

			<button type="submit">Submit</button>
		</div>
	</form>
</main>
<div class="container" id="three-container" />
