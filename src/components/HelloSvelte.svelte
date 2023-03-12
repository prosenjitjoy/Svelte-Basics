<script>
  export let name;
  export let age;

  function increamentAge() {
    age += 1;
  }
</script>

<div class="max-w-lg">
  <h1 class="mb-3 text-xl font-medium text-fuchsia-800">
    Hello {name}, my age is {age}!
  </h1>
  <button
    on:click={increamentAge}
    class="mb-4 rounded-md bg-pink-500 px-5 py-2.5 font-medium text-white"
    >Change Age</button
  >
</div>

