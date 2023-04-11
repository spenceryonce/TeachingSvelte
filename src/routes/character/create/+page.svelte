<script lang="ts">
	let age: number = 37.5;
</script>

<main class="container">
	<h1>Create Character!</h1>

	<form>
		<div class="container">
			<div class="grid">
				<label for="charactername">
					Name
					<input
						type="text"
						id="charactername"
						name="charactername"
						placeholder="Character name"
						required
					/>
				</label>

				<!-- Select -->
				<label for="gender">Gender
					<select id="gender" required>
						<option value="" selected>Select a gender...</option>
						<option value="male">Male</option>
						<option value="female">Female</option>
					</select>
				</label>
			</div>

			<div class="grid">
				<label for="charactername">
					Hair Color
					<input
						type="color"
						id="charactercolor"
						name="charactercolor"
						value="#000000"
					/>
				</label>

				<!-- Select -->
				<label for="buildSel">Build
					<select id="buildSel" required>
						<option value="" selected>Select a build...</option>
						<option value="skinny">Skinny</option>
						<option value="fit">Fit</option>
						<option value="athletic">Athletic</option>
						<option value="greekgod">Greek God</option>
						<option value="bodybuilder">Bodybuilder</option>
						<option value="thick">Thick</option>
						<option value="fat">Fat</option>
					</select>
				</label>
			</div>

			<!-- Range slider -->
			<label for="age"
				>Age: {age}
				<input type="range" min="5" max="80" bind:value={age} id="age" name="age" />
			</label>

			<button type="submit">Submit</button>
		</div>
	</form>
</main>
<div class="container" id="three-container" />
