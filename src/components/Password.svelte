<script>
  let passwords = [];
  let password;
  let isValid = "false";
  let message;
  $: msg = message;
  function addPassword() {
    if (password.trim().length < 5) {
      isValid = "invalid";
      message = "Too Short";
      return;
    }
    if (password.trim().length > 10) {
      isValid = "invalid";
      message = "Too Long";
      return;
    }
    isValid = "true";
    passwords = [...passwords, { id: Math.random(), passwd: password }];
  }
  function deleteItem(id) {
    passwords = passwords.filter(function (el) {
      return el.id != id;
    });
    console.log(id);
  }
</script>

<div class="container p-5">
  <div class="max-w-lg">
    <label for="password" class="mb-2">Password</label>
    <input
      type="text"
      id="password"
      class="mb-4 block w-full border-b-4 bg-gray-50 p-2.5 text-sm text-gray-900 shadow"
      bind:value={password}
    />
    <button
      on:click={addPassword}
      type="button"
      class="rounded-md bg-pink-500 py-2.5 px-5 font-medium text-white"
      >Add Password</button
    >
    <p class:hidden={isValid != "invalid"}>{msg}</p>
  </div>
</div>

{#each passwords as password (password.id)}
  <div class="container p-5">
    <ul>
      <li>
        <button
          type="button"
          class="rounded-md bg-gray-50 py-2.5 px-5 shadow"
          on:click={deleteItem(password.id)}
          >{password.passwd}{password.id}</button
        >
      </li>
    </ul>
  </div>
{/each}
