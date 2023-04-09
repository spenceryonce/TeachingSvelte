<script>
    let age = 37.5;
</script>


<main class="container">
	<h1>Create Character!</h1>

	<form>
		<div class="grid">
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
            <label for="age">Choose your character's Age
                <input type="range" min="5" max="80" bind:value={age} id="age" name="age">
            </label>
            <p>Age: {age}</p>

            <button type="submit">Submit</button>
		</div>
	</form>
</main>
