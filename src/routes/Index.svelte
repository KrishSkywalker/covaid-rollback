<script>
    // Components import
	import * as animateScroll from "svelte-scrollto";

	let errorMessage = "There has been an internal server error due to the Potion API, please check back again"

	// Oxygen beds
	let oxygenBed = false;
	// const fetchOxygenBeds = (async () => {
	// 	var response = await fetch('https://potion-api.vercel.app/table?id=e380bca0e75a4c55bed1578814d13057')
	// 	return await response.json()
	// })()

	// Ventilator beds
	let ventilatorBed = false;
	// const fetchVentilatorBeds = (async () => {
	// 	var response = await fetch('https://potion-api.vercel.app/table?id=dccc5d04ad98429a9a1c75823630a83f')
	// 	return await response.json()
	// })()

	// Oxygen cylinders
	let oxygenCylinder = false;
	// const fetchOxygenCylinders = (async () => {
	// 	var response = await fetch('https://potion-api.vercel.app/table?id=997092406733487cb1a352096c9f3c72')
	// 	return await response.json()
	// })()

	// Oxygen concentrators
	let oxygenConcentrator = false;
	// const fetchOxygenConcentrators = (async () => {
	// 	var response = await fetch('https://potion-api.vercel.app/table?id=d69f983ea0664bfb90a158cc8f96b2b0')
	// 	return await response.json()
	// })()

	// Remdesivir
	let remdesivir = false;
	// const fetchRemdesivirs = (async () => {
	// 	var response = await fetch('https://potion-api.vercel.app/table?id=c728381206034556af52c7f539fd03cd')
	// 	return await response.json()
	// })()

	// Tocilizumab
	let tocilizumab = false;
	// const fetchTocilizumabs = (async () => {
	// 	var response = await fetch('https://potion-api.vercel.app/table?id=21eac0559fc54048a89c48e1aea898b3')
	// 	return await response.json()
	// })()

	// Itolizumab
	let itolizumab = false;
	// const fetchItolizumabs = (async () => {
	// 	var response = await fetch('https://potion-api.vercel.app/table?id=3e4d3d1691634ed29586fa7b3bebc64a')
	// 	return await response.json()
	// })()

	// Ivermecin
	let ivermetcin = false;
	// const fetchIvermecins = (async () => {
	// 	var response = await fetch('https://potion-api.vercel.app/table?id=82f0b893f2ff4dbaba1514fada041946')
	// 	return await response.json()
	// })()

	// Methylprednisolone
	let methylprednisolone = false;
	// const fetchMethylprednisolones = (async () => {
	// 	var response = await fetch('https://potion-api.vercel.app/table?id=97dceaaeff3a48fe9b4dec35cfb0ddc7')
	// 	return await response.json()
	// })()

	// FabiFlu
	let fabiflu = false;
	// const fetchFabiflus = (async () => {
	// 	var response = await fetch('https://potion-api.vercel.app/table?id=a40064e9f7c440de9752fe239adfdb85')
	// 	return await response.json()
	// })()

	// Favipiravir
	let favipiravir = false;
	// const fetchFavipiravir = (async () => {
	// 	var response = await fetch('https://potion-api.vercel.app/table?id=db78c9c770e24ea7945dcfd257effc3f')
	// 	return await response.json()
	// })()

	// Home ICU
	let homeICU = false;
	// const fetchHomeICUs = (async () => {
	// 	var response = await fetch('https://potion-api.vercel.app/table?id=86b0e8c1da434c8e95e12d5a2724da45')
	// 	return await response.json()
	// })()

	// Food Services
	let food = false;
	// const fetchFood = (async () => {
	// 	var response = await fetch('https://potion-api.vercel.app/table?id=4a729eb78021409fa44c5082693fbd4a')
	// 	return await response.json()
	// })()
	

	// Final Twitter request

var search;
var query;

function twitterDeploy() {
  search = []
  query = "https://twitter.com/search?q=verified+delhi+"
  var needs = [
    {
      "name": "Oxygen Bed",
      "need": oxygenBed,
      "query": "oxygen+(bed+OR+beds)"
    },
    {
      "name": "Ventilator",
      "need": ventilatorBed,
      "query": "ventilator+OR+ventilators"
    },
    {
      "name": "Oxygen Cylinder",
      "need": oxygenCylinder,
      "query": "oxygen+OR+oxygen+cylinder"
    },
    {
      "name": "Oxygen Concentrator",
      "need": oxygenConcentrator,
      "query": "(oxygen+concentrator)+OR+concentrator"
    },
    {
      "name": "Remdesivir",
      "need": remdesivir,
      "query": "remdesivir"
    },
    {
      "name": "Tocilizumab",
      "need": tocilizumab,
      "query": "tocilizumab"
    },
    {
      "name": "Itolizumab",
      "need": itolizumab,
      "query": "itolizumab"
    },
    {
      "name": "Ivermectin",
      "need": ivermectin,
      "query": "ivermectin"
    },
    {
      "name": "Methylprednisolone",
      "need": methylprednisolone,
      "query": "methylprednisolone+OR+(methyl+prednisolone)"
    },
    {
      "name": "FabiFlu",
      "need": fabiflu,
      "query": "fabiflu+OR+(fabi+flu)"
    },
	{
      "name": "Favipiravir",
      "need": favipiravir,
      "query": "favipiravir"
    },
    {
      "name": "Home ICU",
      "need": homeICU,
      "query": "(home+icu)+OR+(home+nursing)"
    },
    {
      "name": "Food Service",
      "need": food,
      "query": "(home+food)+OR+(home+service)+OR(food+service)"
    }
  ]

  for (var i = 0; i < needs.length; i++) {
    if (needs[i].need == true) { 
      search[search.length] = i
    }
  }

  for (var j = 0; j < search.length; j++) {
    if ((search.length == 1) || (j == (search.length-  1))) {
      query += needs[search[j]].query + "+"
    }
    else {
      query += needs[search[j]].query + "+OR+"
    }
  }
 
  query += `-"not+verified"+-"unverified"+-"needed"+-"need"+-"required"+-"urgent"+-"asap"+-"urgently"&f=live`
  console.log("Query: " + query)

  window.open(query, '_blank').focus()
  console.log("Twitter search deployed")

}

</script>

<section>
	<div class="width-restriction">
		<h1>I am looking for</h1>
		<p><strong>Currently operational in Delhi and NCR only</strong></p>
		<br/>
		<p>Kindly check all the items you're looking for however selecting more than 4 items would result in an inefficient Twitter Search.</p>
		<section class="checkboxes">
			<div class="row">
				<div class="col-3">
					<div class="card">
						<div class="width-restriction">
							<h3>🏥 Beds</h3>
							<input type=checkbox id="bed-oxygen" bind:checked={oxygenBed}/>
							<label for="bed-oxygen">
								With Oxygen
							</label><br/>

							<input type="checkbox" id="bed-ventilator" bind:checked={ventilatorBed}/>
							<label for="bed-ventilator">
								With Ventilator
							</label><br/>
						</div>
					</div>
					<div class="card">
						<div class="width-restriction">
							<h3>😷 Oxygen</h3>
							<input type=checkbox id="oxygen-cylinder" bind:checked={oxygenCylinder}/>
							<label for="oxygen-cylinder">
								Oxygen Cylinder
							</label><br/>

							<input type="checkbox" id="oxygen-concentrator" bind:checked={oxygenConcentrator}/>
							<label for="oxygen-concentrator">
								Oxygen Concentrator
							</label><br/>
						</div>
					</div>
				</div>

				<div class="col-3">
					<div class="card">
						<div class="width-restriction">
							<h3>💊 Injections & Medicines</h3>

							<h4>Injections</h4>
							
							<input type=checkbox id="remdesivir" bind:checked={remdesivir}/>
							<label for="remdesivir">
								Remdesivir
							</label><br/>

							<input type="checkbox" id="tocilizumab" bind:checked={tocilizumab}/>
							<label for="tocilizumab">
								Tocilizumab
							</label><br/>

							<input type="checkbox" id="itolizumab" bind:checked={itolizumab}/>
							<label for="itolizumab">
								Itolizumab
							</label><br/>

							<h4>Medicines</h4>

							<input type=checkbox id="ivermectin" bind:checked={ivermetcin}/>
							<label for="ivermectin">
								Ivermectin
							</label><br/>

							<input type="checkbox" id="methylprednisolone" bind:checked={methylprednisolone}/>
							<label for="methylprednisolone">
								Methylprednisolone
							</label><br/>

							<input type="checkbox" id="fabiFlu" bind:checked={fabiflu}/>
							<label for="fabiFlu">
								FabiFlu
							</label><br/>

							<input type="checkbox" id="favipiravir" bind:checked={favipiravir}/>
							<label for="favipiravir">
								Favipiravir
							</label><br/>
						</div>
					</div>
				</div>

				<div class="col-3">
					<div class="card">
						<div class="width-restriction">
							<h3>🍴 Home ICU & Food Services</h3>

							<input type=checkbox id="homeICU" bind:checked={homeICU}/>
							<label for="homeICU">
								Home ICU
							</label><br/>

							<input type="checkbox" id="foodServices" bind:checked={food}/>
							<label for="foodServices">
								Food services
							</label><br/>
						</div>
					</div>
				</div>
			</div>
		</section>
		

		<!-- Add post-req section -->
		<section class="post-request">
			<h1>Post your request</h1>
			<div class="post-buttons">
				<button on:click={twitterDeploy}>
					<p><strong>
						Search the latest leads on Twitter
					</strong></p>
				</button>
				<button on:click={() => animateScroll.scrollTo({element: '#notion-resources', offset: -100})}>
					<p><strong>
						Search verified leads on our database
					</strong></p>
				</button>
			</div>
		</section>
		<br/><br/><br/>


		<!-- Manual DB section -->
		<h1 id="notion-resources">Resources from our personally-verified database</h1>
		<br/>
		
		<!-- Oxygen Beds -->
		{#if oxygenBed}
		<h2>Oxygen Beds</h2>
		<br/>
		<p>Link to the Oxygen beds database: 
			<a href="https://www.notion.so/krishgoel/e380bca0e75a4c55bed1578814d13057?v=d9969c2a9b8547f99eeec784f091cd43">Oxygen beds</a>
		</p>
		<br/>
		{/if}

		<!-- Ventilator Beds -->
		{#if ventilatorBed}
		<h2>Ventilator Beds</h2>
		<br/>
		<p>Link to the Ventilator beds database: 
			<a href="https://www.notion.so/krishgoel/dccc5d04ad98429a9a1c75823630a83f?v=9f6005edcad04c9bb69288a09243b6e9">Oxygen beds</a>
		</p>
		<br/>
		{/if}

		<!-- Oxygen Cylinder -->
		{#if oxygenCylinder}
		<h2>Oxygen Cylinders</h2>
		<br/>
		<p>Link to the Oxygen Cylinders database: 
			<a href="https://www.notion.so/krishgoel/997092406733487cb1a352096c9f3c72?v=a50b4663f6fe45fabfee882ea35b8515">Oxygen Cylinders</a>
		</p>
		<br/>
		{/if}
		
		<!-- Oxygen Concentrator -->
		{#if oxygenConcentrator}
		<h2>Oxygen Concentrators</h2>
		<br/>
		<p>Link to the Oxygen Concentrators database: 
			<a href="https://www.notion.so/krishgoel/d69f983ea0664bfb90a158cc8f96b2b0?v=b12c7923ee284f909c12358f795c3115">Oxygen Concentrators</a>
		</p>
		<br/>
		{/if}

		<!-- Remdesivir -->
		{#if remdesivir}
		<h2>Remdesivir Injections</h2>
		<br/>
		<p>Link to the Remdesivir Injections database: 
			<a href="https://www.notion.so/krishgoel/c728381206034556af52c7f539fd03cd?v=13af84b794cb4f9bb83a9b5f43ed7553">Remdesivir Injections</a>
		</p>
		<br/>
		{/if}

		<!-- Tocilizumab -->
		{#if tocilizumab}
		<h2>Tocilizumab Injections</h2>
		<br/>
		<p>Link to the Tocilizumab Injections database: 
			<a href="https://www.notion.so/krishgoel/21eac0559fc54048a89c48e1aea898b3?v=1173fcb70778446e9245d82f0953ea48">Tocilizumab Injections</a>
		</p>
		<br/>
		{/if}
		
		<!-- Itolizumab -->
		{#if itolizumab}
		<h2>Itolizumab Injections</h2>
		<br/>
		<p>Link to the Itolizumab Injections database: 
			<a href="https://www.notion.so/krishgoel/3e4d3d1691634ed29586fa7b3bebc64a?v=e073b396b6ab46d09dc565db8d36185b">Itolizumab Injections</a>
		</p>
		<br/>
		{/if}

		<!-- Ivermectin -->
		{#if ivermetcin}
		<h2>Ivermectin Injections</h2>
		<br/>
		<p>Link to the Ivermectin Injections database: 
			<a href="https://www.notion.so/krishgoel/82f0b893f2ff4dbaba1514fada041946?v=76c1a2938ba64a22acd89ba9513d2cb8">Ivermectin Injections</a>
		</p>
		<br/>
		{/if}

		<!-- Methylprednisolone -->
		{#if methylprednisolone}
		<h2>Methylprednisolone Injections</h2>
		<br/>
		<p>Link to the Methylprednisolone Injections database: 
			<a href="https://www.notion.so/krishgoel/97dceaaeff3a48fe9b4dec35cfb0ddc7?v=b3f82e9fd4c2482499b1955697cfe2cf">Methylprednisolone Injections</a>
		</p>
		<br/>
		{/if}

		<!-- FabiFlu -->
		{#if fabiflu}
		<h2>FabiFlu</h2>
		<br/>
		<p>Link to the FabiFlu database: 
			<a href="https://www.notion.so/krishgoel/a40064e9f7c440de9752fe239adfdb85?v=3ca55222894e4b609819abb7b0fead35">FabiFlu</a>
		</p>
		<br/>
		{/if}

		<!-- Favipiravir -->
		{#if favipiravir}
		<h2>Favipiravir</h2>
		<br/>
		<p>Link to the Favipiravir database: 
			<a href="https://www.notion.so/krishgoel/db78c9c770e24ea7945dcfd257effc3f?v=d6414dbe785c4ac4958aacf50fe2ea6b">Favipiravir</a>
		</p>
		<br/>
		{/if}

		<!-- Home ICU -->
		{#if homeICU}
		<h2>Home ICU</h2>
		<br/>
		<p>Link to the Home ICU database: 
			<a href="https://www.notion.so/krishgoel/86b0e8c1da434c8e95e12d5a2724da45?v=aaccf9c4c76643e3b93ccf2997b235bc">Home ICU Services</a>
		</p>
		<br/>
		{/if}

		<!-- Food Services -->
		{#if food}
		<h2>Food Services</h2>
		<br/>
		<p>Link to the Food Services database: 
			<a href="https://www.notion.so/krishgoel/4a729eb78021409fa44c5082693fbd4a?v=11c07f8dcdeb403cb3a0addeec83d1b3">Food Services</a>
		</p>
		<br/>
		{/if}

	</div>
</section>