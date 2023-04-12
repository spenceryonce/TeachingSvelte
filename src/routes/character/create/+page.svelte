<script lang="ts">
	import { onMount } from "svelte";
	let age: number = 37.5;
	let characterName = '';
	let characterGender = '';
	let characterHair = '';
	let characterBuild = '';
	let characterEyeColor = '';
	let characterSkinColor = '';
	let characterHairStyle = '';
	let characterFacialHairStyle = '';
	let characterClothingStyle = '';
	let characterOccupation = '';
	let characterHobbies = [];
	let characterWeapon = '';
	let characterAge = '';


	let charNameEl;
	let charGenderEl;
	let charHairEl;
	let charBuildEl;
	let charEyeColorEl;
	let charSkinColorEl;
	let charHairStyleEl;
	let charFacialHairStyleEl;
	let charClothingStyleEl;
	let charOccupationEl;
	let charHobbiesEl;
	let charWeaponEl;
	let charAgeEl;

	class Character {
		public name;
		public gender;
		public hair;
		public build;
		public eyeColor;
		public skinColor;
		public hairStyle;
		public facialHairStyle;
		public clothingStyle;
		public occupation;
		public hobbies;
		public age;
		public weapon;
		constructor(name: string,gender: string,hair: string,build: string,eyeColor: string,skinColor: string,hairStyle: string,facialHairStyle: string,clothingStyle:string,occupation:string,hobbies:Array<string>,weapon:string,age:string){
			this.name = name;
			this.gender = gender;
			this.hair = hair;
			this.build = build;
			this.eyeColor = eyeColor;
			this.skinColor = skinColor;
			this.hairStyle = hairStyle;
			this.facialHairStyle = facialHairStyle;
			this.clothingStyle = clothingStyle;
			this.occupation = occupation;
			this.hobbies = hobbies;
			this.weapon = weapon;
			this.age = age;
			
		}
	}
	function createCharacter(){
		charNameEl = document.getElementById("charactername") as HTMLInputElement;
		charGenderEl = document.getElementById("gender") as HTMLInputElement;
		charHairEl = document.getElementById("haircolor") as HTMLInputElement;
		charBuildEl = document.getElementById("buildSel") as HTMLInputElement;
		charEyeColorEl = document.getElementById("eyecolor") as HTMLInputElement;
		charSkinColorEl = document.getElementById("skincolor") as HTMLInputElement;
		charHairStyleEl = document.getElementById("hairSel") as HTMLInputElement;
		charFacialHairStyleEl = document.getElementById("facialHairSel") as HTMLInputElement;
		charClothingStyleEl = document.getElementById("clothingStyleSel") as HTMLInputElement;
		charOccupationEl = document.getElementById("occupationSel") as HTMLInputElement;
		charHobbiesEl = document.getElementById("hobbies");
		charWeaponEl = document.getElementById("weaponSel") as HTMLInputElement;
		charAgeEl = document.getElementById("age") as HTMLInputElement;

		let char = new Character(charNameEl.value,charGenderEl.value,charHairEl.value,charBuildEl.value,charEyeColorEl.value,charSkinColorEl.value,charHairStyleEl.value,charFacialHairStyleEl.value,charClothingStyleEl.value,charOccupationEl.value,[],charWeaponEl.value,age.toString());

		console.log(char);

		characterName = charNameEl.value;
		characterGender = charGenderEl.value;
		characterHair = charHairEl.value;
		characterBuild = charBuildEl.value;
		characterEyeColor = charEyeColorEl.value;
		characterSkinColor = charSkinColorEl.value;
		characterHairStyle = charHairStyleEl.value;
		characterFacialHairStyle = charFacialHairStyleEl.value;
		characterClothingStyle = charClothingStyleEl.value;
		characterOccupation = charOccupationEl.value;
		// characterHobbies = charHobbiesEl.value;
		characterWeapon = charWeaponEl.value;
		characterAge = charAgeEl.value;
	}

	
</script>

<main class="container">
	<h1>Create A Character!</h1>

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
				<label for="gender">Gender
					<select id="gender" required>
						<option value="" selected>Select a gender...</option>
						<option value="male">Male</option>
						<option value="female">Female</option>
					</select>
				</label>
			</div>
			<div class="grid">
				<label for="haircolor">
					Hair Color
					<input
						type="color"
						id="haircolor"
						name="haircolor"
						value="#000000"
					/>
				</label>
				<label for="buildSel">Build
					<select id="buildSel" required placeholder="">
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
			<div class="grid">
				<label for="eyecolor">
					Eye Color
					<input
						type="color"
						id="eyecolor"
						name="eyecolor"
						value="#000000"
					/>
				</label>
				<label for="skincolor">
					Skin Color
					<input
						type="color"
						id="skincolor"
						name="skincolor"
						value="#000000"
					/>
				</label>
			</div>
			<div class="grid">
				<label for="hairSel">
					Hair
					<select id="hairSel">
						<option value="" selected>Select a hair style...</option>
						<option value="bald">Bald</option>
						<option value="closecut">Close Cut</option>
						<option value="short">Short</option>
						<option value="long">Long</option>
						<option value="afro">Afro</option>
						<option value="mohawk">Mohawk</option>
						<option value="mullet">Mullet</option>
						<option value="business">Business</option>
					</select>
				</label>
				<label for="facialHairSel">
					Facial Hair
					<select id="facialHairSel">
						<option value="" selected>Select a facial hair style...</option>
						<option value="none">None</option>
						<option value="cleanshaven">Clean Shaven</option>
						<option value="stubble">Stubble</option>
						<option value="closecut">Close Cut</option>
						<option value="beard">Beard</option>
						<option value="longbeard">Long Beard</option>
						<option value="monk">Monk</option>
					</select>
				</label>
			</div>
			<div class="grid">
				<label for="clothingStyleSel">
					Clothing Style
					<select id="clothingStyleSel">
						<option value="" selected>Select a clothing style...</option>
						<option value="peasant">Peasant</option>
						<option value="worker">Worker</option>
						<option value="blacksmith">Blacksmith</option>
						<option value="royal">Royal</option>
						<option value="modern">Modern</option>
						<option value="athletic">Athletic</option>
						<option value="warrior">Warrior</option>
						<option value="knight">Knight</option>
					</select>
				</label>
				<label for="occupationSel">
					Occupation
					<select id="occupationSel">
						<option value="" selected>Select an occupation...</option>
						<option value="">None</option>
						<option value="blacksmith">Clean Shaven</option>
						<option value="seamstress">Seamstress</option>
						<option value="banker">Banker</option>
						<option value="businessman">Businessman</option>
						<option value="king">King</option>
						<option value="queen">Queen</option>
						<option value="messenger">Messenger</option>
						<option value="knight">Knight</option>
						<option value="warrior">Warrior</option>
						<option value="ringfighter">Ring Fighter</option>
						<option value="runner">Runner</option>
						<option value="celebrity">Celebrity</option>
					</select>
				</label>
			</div>
			<div class="grid">
				<label for="hobbiesSel">
					Hobbies
					<details role="list" id="hobbiesSel">
						<summary aria-haspopup="listbox">Select any hobbies...</summary>
						<ul role="listbox">
							<li>
								<label>
								<input type="checkbox">
								Drawing
								</label>
							</li>
							<li>
								<label>
								<input type="checkbox">
								Painting
								</label>
							</li>
							<li>
								<label>
								<input type="checkbox">
								Running
								</label>
							</li>
							<li>
								<label>
								<input type="checkbox">
								Eating
								</label>
							</li>
							<li>
								<label>
								<input type="checkbox">
								Gardening
								</label>
							</li>
							<li>
								<label>
								<input type="checkbox">
								Working Out
								</label>
							</li>
							<li>
								<label>
								<input type="checkbox">
								Chess
								</label>
							</li>
							<li>
								<label>
								<input type="checkbox">
								People Games
								</label>
							</li>
							<li>
								<label>
								<input type="checkbox">
								Mind Games
								</label>
							</li>
							<li>
								<label>
								<input type="checkbox">
								Cards
								</label>
							</li>
						</ul>
					</details>
				</label>
				<label for="weaponSel">
					Weapon
					<select id="weaponSel">
						<option value="" selected>Select a weapon...</option>
						<option value="broom">Broom</option>
						<option value="sword">Sword</option>
						<option value="dagger">Dagger</option>
						<option value="mace">Mace</option>
						<option value="spear">Spear</option>
						<option value="machete">Machete</option>
						<option value="axe">Axe</option>
						<option value="throwingstars">Throwing Stars</option>
						<option value="fists">Fists</option>
						<option value="pepperspray">Pepper Spray</option>
						<option value="musket">Musket</option>
						<option value="laser">Laser</option>
					</select>
				</label>
			</div>

			<!-- Range slider -->
			<label for="age"
				>Age: {age}
				<input type="range" min="5" max="80" bind:value={age} id="age" name="age" />
			</label>

			<button type="submit" on:click|preventDefault={createCharacter}>Submit</button>
		</div>
	</form>

	<article>
		<header>{characterName != '' ? characterName : 'Generating Character...'}</header>
		{#if characterName != ''}
			{characterGender != '' ? `Build: ${characterGender}` : ''}
			{characterHairStyle != '' ? `Hair Style: ${characterHairStyle}` : ''}
			{characterFacialHairStyle != '' ? `Facial Hair Style: ${characterFacialHairStyle}` : ''}
			{characterClothingStyle != '' ? `Clothing Style: ${characterClothingStyle}` : ''}
			{characterOccupation != '' ? `Occupation: ${characterOccupation}` : ''}
			{characterWeapon != '' ? `Weapon: ${characterWeapon}` : ''}
			{characterAge != '' ? `Age: ${characterAge}` : ''}
			{characterBuild != '' ? `Build: ${characterBuild}` : ''}
		{/if}
	</article>
</main>
<div class="container" id="three-container" />
