<script>
  const name = "chiku";
  const channel = "<b>Code Testing</b>";
  const headingId = "heading";
  const id = "tooId";
  const disabled = true;
  const status = "sccuess";
  const isPromoted = true;
  const promoted = true;
  // conditional rendering
  const num = 0;
  // list rendering
  const names = ["rush", "dyna", "clerk"];
  const fullNames = [
    { first: "Bruse", last: "Wayne" },
    { first: "Clark", last: "Kent" },
    { first: "Princess", last: "Diana" },
  ];
  // event handling
  let count = 0;
  function handleClick(event) {
    console.log(event);
    count += 1;
  }
  function incrementByFive(stepSize) {
    count += stepSize;
  }
  // form
  const formValues = {
    name: "",
    profileSummary: "",
    country: "",
    jobLocation: [],
    remoteWork: false,
    skillSets: [],
    yearsOfExperience: "",
  };

  function submitForm(event) {
    // event.preventDefault();
    console.log(formValues);
  }
</script>

<main>
  <div>
    <pre>{JSON.stringify(formValues, null, 2)}</pre>
  </div>
  <!-- form -->
  <!-- on submit preventDefault modifiers -->
  <form on:submit|preventDefault={submitForm}>
    <div>
      <label for="name">Name</label>
      <input type="text" id="name" bind:value={formValues.name} />
    </div>
    <div>
      <label for="profile">Profile Summary</label>
      <textarea
        id="profile"
        cols="30"
        rows="5"
        bind:value={formValues.profileSummary}
      />
    </div>
    <div>
      <label for="country">Country</label>
      <select id="country" bind:value={formValues.country}>
        <option value="">Select a country</option>
        <option value="india">India</option>
        <option value="vietnam">Vietnam</option>
        <option value="singapore">Singapore</option>
      </select>
    </div>
    <div>
      <label for="job-location">Job Location</label>
      <select id="job-location" bind:value={formValues.jobLocation} multiple>
        <option value="">Select a country</option>
        <option value="india">India</option>
        <option value="vietnam">Vietnam</option>
        <option value="singapore">Singapore</option>
      </select>
    </div>
    <div>
      <input
        type="checkbox"
        name="remoteWork"
        id="remoteWork"
        bind:checked={formValues.remoteWork}
      />
      <label for="remoteWork">Open to remote work?</label>
    </div>
    <div>
      <label>Skill set</label>
      <input
        type="checkbox"
        id="html"
        value="html"
        bind:group={formValues.skillSets}
      />
      <label for="html">HTML</label>
      <input
        type="checkbox"
        id="css"
        value="css"
        bind:group={formValues.skillSets}
      />
      <label for="css">CSS</label>
      <input
        type="checkbox"
        id="javascript"
        value="javascript"
        bind:group={formValues.skillSets}
      />
      <label for="javascript">Javascript</label>
    </div>
    <div>
      <label>Years of Experience</label>
      <input
        type="radio"
        id="0-2"
        value="0-2"
        bind:group={formValues.yearsOfExperience}
      />
      <label for="0-2">0-2</label>
      <input
        type="radio"
        id="3-5"
        value="3-5"
        bind:group={formValues.yearsOfExperience}
      />
      <label for="3-5">3-5</label>
      <input
        type="radio"
        id="6-10"
        value="6-10"
        bind:group={formValues.yearsOfExperience}
      />
      <label for="6-10">6-10</label>
    </div>
    <button>Submit</button>
  </form>
  <h1>Hello {name}</h1>
  <h2>{@html channel}</h2>
  <h2 id={headingId}>This is a heading</h2>
  <h3 {id}>New Style id</h3>
  <button {disabled}>Bind</button>
  <h4 class="underline">Woh ku</h4>
  <h2 class={status}>Status</h2>
  <h3 class={isPromoted ? "promoted" : "non-promoted"}>Dynamic Styling</h3>
  <h3 class:promoted={isPromoted}>Dynamic Style2</h3>
  <!-- short hand properties -->
  <h3 class:promoted>Dynamic Style3</h3>
  <!-- conditional rendering -->
  {#if num === 0}
    <h2>The number is zero.</h2>
  {:else if num > 0}
    <h2>The number is positive.</h2>
  {:else if num < 0}
    <h2>The number is negative.</h2>
  {:else}
    <h2>Not a number.</h2>
  {/if}
  <!-- list rendering -->
  <!-- here key is (name) -->
  {#each names as name, index (name)}
    <h2>{index + 1}.{name}</h2>
  {/each}
  <!-- each -->
  {#each fullNames as name, index (name)}
    <h2>{index + 1} {name.first} {name.last}</h2>
  {/each}
  <!-- event -->
  <button on:click={() => (count = count + 1)}>Count {count}</button>
  <button on:click={handleClick}>Count 2nd {count}</button>
  <button on:click={() => incrementByFive(5)}>Count 3rd {count}</button>
</main>

<style>
  input + label {
    display: inline-flex;
  }
  main {
    /* text-align: center; */
    padding: 1em;
    max-width: 240px;
    margin: 0 auto;
  }

  h1 {
    color: #ff3e00;
    text-transform: uppercase;
    font-size: 4em;
    font-weight: 100;
  }

  .underline {
    text-decoration: underline;
  }

  .promoted {
    text-decoration: overline;
  }

  .non-promoted {
    text-decoration: dotted;
    background-color: #ff3e00;
  }

  .danger {
    color: #ff3e00;
  }

  .sccuess {
    color: olive;
  }

  @media (min-width: 640px) {
    main {
      max-width: none;
    }
  }
</style>
