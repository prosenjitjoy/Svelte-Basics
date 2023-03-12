<script>
  export let userName = "Joy";
  export let jobTitle = "";
  export let description = "";
  export let imageSource = "";

  const initialName = userName;

  let formState = "empty";
  let createdContacts = [];

  function addContact() {
    if (
      userName.trim().length == 0 ||
      jobTitle.trim().length == 0 ||
      imageSource.trim().length == 0 ||
      description.trim().length == 0
    ) {
      formState = "invalid";
      return;
    }
    formState = "done";
    createdContacts = [
      ...createdContacts,
      {
        id: Math.random(),
        name: userName,
        title: jobTitle,
        imageUrl: imageSource,
        desc: description,
      },
    ];
  }

  function deleteFirst() {
    createdContacts = createdContacts.slice(1);
  }
  function deleteLast() {
    createdContacts = createdContacts.slice(0, -1);
  }
</script>

<div class="max-w-lg">
  <label for="userName" class="mb-2">User Name</label>
  <input
    type="text"
    id="userName"
    class="mb-4 block w-full border-b-4  bg-gray-50 p-2.5 text-sm text-gray-900 shadow"
    bind:value={userName}
  />

  <label for="jobTitle" class="mb-2">Job Title</label>
  <input
    type="text"
    id="jobTitle"
    class="mb-4 block w-full border-b-4 bg-gray-50 p-2.5 text-sm text-gray-900 shadow"
    bind:value={jobTitle}
  />

  <label for="imageURL" class="mb-2">Image URL</label>
  <input
    type="text"
    id="imageURL"
    class="mb-4 block w-full border-b-4 bg-gray-50 p-2.5 text-sm text-gray-900 shadow"
    bind:value={imageSource}
  />

  <label for="description" class="mb-2">Description</label>
  <textarea
    id="description"
    class="mb-4 block w-full border-b-4 bg-gray-50 p-2.5 text-sm text-gray-900 shadow"
    bind:value={description}
  />

  <button
    on:click|once={addContact}
    class="mb-4 rounded-md bg-pink-500 px-5 py-2.5 font-medium text-white"
    >Add Contact Card</button
  >
  <button
    on:click={deleteFirst}
    class="mb-4 rounded-md bg-pink-500 px-5 py-2.5 font-medium text-white"
    >Delete First</button
  >
  <button
    on:click={deleteLast}
    class="mb-4 rounded-md bg-pink-500 px-5 py-2.5 font-medium text-white"
    >Delete Last</button
  >
</div>

{#if formState === "invalid"}
  <p>Invalid Input</p>
{:else}
  <p>Please enter some data and hit the button!</p>
{/if}

{#each createdContacts as contact, index (contact.id)}
  <div
    class="max-w-lg overflow-hidden rounded-lg border border-gray-200 bg-white shadow"
  >
    <h2># {index}</h2>
    <header class="item flex items-center gap-4">
      <div class="flex h-32 w-40 items-center justify-center bg-gray-300">
        <img
          src={contact.imageUrl}
          alt={contact.name}
          width="120"
          height="96"
        />
      </div>
      <div>
        <h1 class="mb-4 text-lg font-medium">{contact.name} / {initialName}</h1>
        <h2 class="text-sm font-normal text-gray-500">{contact.title}</h2>
      </div>
    </header>
    <hr class="h-px border-0 bg-gray-200 dark:bg-gray-700" />
    <div class="py-3">
      <p>{contact.desc}</p>
    </div>
  </div>
{:else}
  <p>Please start adding some contacts, wee found none</p>
{/each}
