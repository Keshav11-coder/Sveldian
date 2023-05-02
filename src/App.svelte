<script>
	import Close from "./Close.svelte";
	import Hello from "./Hello.svelte";
	import Gi2Div from "./Gi2-div.svelte";
	import Gi1Div from "./Gi1-div.svelte";
	import Suggested from "./Suggested.svelte";
	import Sfi from "./Suggested-fillIn.svelte";
	let includeSkip = false;
	let index = 0;
	let activatorValue = 0;

	//keyboard accessibility

	function handleKeyDown(event) {
		if (event.key === "Enter" || event.key === " ") {
			index =
				index != 4
					? (index = index + 1)
					: index == 4
					? (index = 4)
					: (index = index);
		}
	}

	const deviceWidth = window.innerWidth;

	function redirect() {
		window.location.href =
			"https://keshav11-coder.github.io/Skilldian/explore/explore.html";
	}

	function changeskip(bool) {
		includeSkip = bool;
	}
</script>

<div class="document" id="doc">
	<Close Value={!activatorValue} bind:activatorValue />
	<Hello Value={activatorValue} wtext={"hello"} />
	<div class="container-1 {!activatorValue ? '' : 'container-2'}" id="c1">
		<div class="wrapper" id="wf">
			{#if index == 0}
				<div class="a" id="af">
					<Gi2Div
						gi1="first name"
						gi2="last name"
						gi1t="text"
						gi2t="text"
						gi1max={200}
						gi2max={200}
					/>
					<Sfi Value={activatorValue} {index} />
				</div>
			{:else if index == 1}
				{changeskip(true)}
				<div class="a1" id="af">
					<Gi2Div
						gi1="email"
						gi2="phone number"
						gi1t="email"
						gi2t="number"
						gi1max={200}
						gi2max={7}
						skip={includeSkip}
					/>
					<Sfi Value={activatorValue} {index} />
				</div>
			{:else if index == 2}
				{changeskip(false)}
				<div class="a1" id="af">
					<div
						class="description {activatorValue
							? ''
							: 'description-da'}"
					>
						<h3 class="--description">Tell us about yourself</h3>
						<h4 class="--description-sub">
							So we can demo how Skilldian gets you your dream
							job!
						</h4>
					</div>
					<Gi1Div
						gi="click here"
						activator={true}
						bind:activatorValue
					/>
					{#if deviceWidth < 1000}
						<!---->
					{:else if deviceWidth > 1000}
						<Sfi Value={activatorValue} {index} />
					{/if}
				</div>
			{:else if index == 3}
				{changeskip(false)}
				<div class="a1" id="af">
					<div
						class="description {activatorValue
							? ''
							: 'description-da'}"
					>
						<h3 class="--description">
							Tell us about your profession
						</h3>
						<h4 class="--description-sub">
							What do you like to do? What do you prefer doing?
						</h4>
					</div>
					<Gi1Div
						gi="your profession"
						activator={true}
						bind:activatorValue
					/>
					{#if deviceWidth < 1000}
						<Suggested Value={activatorValue} />
					{:else if deviceWidth > 1000}
						<Sfi Value={activatorValue} {index} />
					{/if}
				</div>
			{:else if index == 4}
				{changeskip(true)}
				<div class="a1" id="af">
					<div
						class="description {activatorValue
							? ''
							: 'description-da'}"
					>
						<h3 class="--description">Give us a hint!</h3>
						<h4 class="--description-sub">What are your skills?</h4>
					</div>
					<Gi1Div gi="skills" activator={true} bind:activatorValue />
					{#if deviceWidth < 1000}
						<Suggested Value={activatorValue} />
					{:else if deviceWidth > 1000}
						<Sfi Value={activatorValue} {index} />
					{/if}
				</div>
			{/if}

			{#if includeSkip == false}
				<div class="t-forw" id="tf">
					{#if index != 4}
						<div
							class="forw btn"
							on:click={() =>
								index != 4
									? (index = index + 1)
									: index == 4
									? (index = 4)
									: (index = index)}
							on:keydown={handleKeyDown}
						>
							<h3 class="bl">next</h3>
						</div>
					{:else if index == 4}
						<div
							class="forw btn"
							on:click={redirect}
							on:keydown={handleKeyDown}
						>
							<h3 class="bl">finish</h3>
						</div>
					{/if}
				</div>
			{:else if includeSkip == true}
				<div class="t-forw2" id="tf">
					{#if index != 4}
						<div
							class="forw btn"
							on:click={() =>
								index != 4
									? (index = index + 1)
									: index == 4
									? (index = 4)
									: (index = index)}
							on:keydown={handleKeyDown}
						>
							<h3 class="bl">next</h3>
						</div>
						<div class="skip btn">
							<h3 class="ppl">skip</h3>
						</div>
					{:else if index == 4}
						<div
							class="forw btn"
							on:click={redirect}
							on:keydown={handleKeyDown}
						>
							<h3 class="bl">finish</h3>
						</div>
						<div class="skip btn">
							<h3 class="ppl">skip</h3>
						</div>
					{/if}
				</div>
			{/if}
		</div>
	</div>
</div>

<style>
	* {
		margin: 0;
		padding: 0;
	}

	@media (prefers-color-scheme: dark) {
		:root {
			--forwC: rgba(85, 51, 235, 0.871);
			--skipC: #ffffffde;
			--oppositeC: black;
		}
	}

	@media (prefers-color-scheme: light) {
		:root {
			--forwC: #5533ebde;
			--skipC: #000000de;
			--oppositeC: white;
		}
	}

	.btn {
		width: 98%;
		height: 60%;
		border-radius: 6px;
		user-select: none;
	}
	.t-forw {
		width: 75%;
		height: 18%;
		display: flex;
		align-items: center;
		justify-content: center;
		flex-direction: column;
		align-self: center;
		position: relative;
	}

	.t-forw2 {
		width: 75%;
		height: 30%;
		display: flex;
		align-items: center;
		justify-content: flex-end;
		flex-direction: column;
		align-self: center;
		z-index: 99;
	}
	.skip {
		border: 3px solid var(--skipC);
		display: flex;
		align-items: center;
		justify-content: center;
		justify-self: flex-end;
		margin-top: 5%;
		z-index: 3;
		cursor: pointer;
		opacity: 45;
	}

	.forw {
		border: 3px solid var(--forwC);
		display: flex;
		justify-content: center;
		align-items: center;
		justify-self: flex-end;
		margin-top: 3%;
		z-index: 3;
		cursor: pointer;
	}

	.document {
		background-color: transparent;
		width: 100%;
		height: 100%;
		position: absolute;
		z-index: 1;
	}

	.container-1 {
		width: 100%;
		height: 70%;
		display: flex;
		margin-top: 18%;
		flex-direction: column;
		position: relative;
		top: 0;
		z-index: 2;

		transition: ease-in-out 0.6s;
	}

	.container-2 {
		height: 70%;
		margin-top: 15%;

		transition: ease-in-out 0.6s;
	}

	.wrapper {
		height: 100%;
		width: 100%;
		display: flex;
		justify-content: flex-start;
		align-self: center;
		justify-self: center;
		flex-direction: column;
		color: var(--oppositeC);
	}

	.a {
		width: 100%;
		height: 100%;
		display: flex;
		align-items: center;
		justify-content: flex-start;
		flex-direction: column;
		transition: ease 1s;
		color: var(--skipC);
	}

	.a1 {
		width: 100%;
		height: 100%;
		display: flex;
		align-items: center;
		justify-content: flex-start;
		flex-direction: column;
		transition: ease 1s;
	}

	::placeholder {
		font-size: 4.8vw;
		color: var(--placeHC);
		opacity: 0.7;
	}

	.ppl {
		font-family: "Montserrat Alternates", sans-serif;
		font-size: 5.4vw;
		color: var(--skipC);
	}

	.bl {
		font-family: "Montserrat Alternates", sans-serif;
		font-size: 5.4vw;
		color: var(--forwC);
	}

	.description {
		width: 100%;
		height: 5%;
		font-family: "Trebuchet MS", "Lucida Sans Unicode", "Lucida Grande",
			"Lucida Sans", Arial, sans-serif;
		color: var(--skipC);
		display: flex;
		align-items: center;
		justify-content: center;
		flex-direction: column;
		opacity: 1;
		transition: ease-in-out 0.4s;
	}

	.description-da {
		opacity: 0;
	}

	.--description {
		font-size: 4vw;
		margin-bottom: 2%;
	}

	.--description-sub {
		font-size: 3.5vw;
		opacity: 0.7;
	}

	@media only screen and (min-width: 1000px) {
		/* For desktop: */
		.container-1 {
			width: 50%;
			margin-top: 3%;
			display: flex;
			align-self: center;
			height: 90%;
			justify-self: center;
		}

		.document {
			background-color: transparent;
			width: 100%;
			height: 100%;
			position: absolute;
			z-index: 1;
			display: flex;
			align-items: flex-start;
			justify-content: flex-start;
			flex-direction: column;
		}

		.btn {
			width: 100%;
			height: 40%;
			border-radius: 6px;
			user-select: none;
		}
		.t-forw {
			width: 15%;
			height: 18%;
			display: flex;
			align-items: center;
			justify-content: flex-start;
			flex-direction: column;
			position: relative;
		}
		.t-forw2 {
			width: 15%;
			height: 18%;
			display: flex;
			align-items: center;
			justify-content: flex-end;
			flex-direction: column;
			align-self: center;
			z-index: 99;
		}

		.skip {
			border: 3px solid var(--skipC);
			display: flex;
			align-items: center;
			justify-content: center;
			justify-self: flex-end;
			z-index: 3;
		}

		.forw {
			border: 3px solid var(--forwC);
			display: flex;
			justify-content: center;
			align-items: center;
			justify-self: center;
			z-index: 3;
		}

		.bl {
			font-family: "Montserrat Alternates", sans-serif;
			font-size: 0.8vw;
			color: var(--forwC);
		}

		.ppl {
			font-family: "Montserrat Alternates", sans-serif;
			font-size: 0.8vw;
			color: var(--skipC);
		}

		.a {
			width: 100%;
			height: 55%;
			display: flex;
			align-items: center;
			justify-content: flex-start;
			flex-direction: column;
			transition: ease 1s;
		}

		.a1 {
			width: 100%;
			height: 45%;
			display: flex;
			align-items: center;
			justify-content: flex-start;
			flex-direction: column;
			transition: ease 1s;
		}

		.description {
			width: 100%;
			height: 5%;
			font-family: "Trebuchet MS", "Lucida Sans Unicode", "Lucida Grande",
				"Lucida Sans", Arial, sans-serif;
			color: var(--skipC);
			display: flex;
			align-items: center;
			justify-content: center;
			flex-direction: column;
			opacity: 1;
			transition: ease-in-out 0.4s;
			margin-bottom: 5%;
		}

		.description-da {
			opacity: 1;
		}

		.--description {
			font-size: 1.0vw;
			margin-bottom: 2%;
		}

		.--description-sub {
			font-size: 0.8vw;
			opacity: 0.7;
		}
	}
</style>
