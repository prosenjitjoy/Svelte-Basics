<script>
  import HelloSvelte from "../components/HelloSvelte.svelte";
  import ContactCard from "../components/ContactCard.svelte";

  export let name;
  export let age;
  let userName;
  let jobTitle;
  let imageSource;
  let description;
  let password;

</script>

<div class="container p-5">
  <HelloSvelte {name} {age}/>
  <ContactCard {userName} {password} {jobTitle} {imageSource} {description} />
</div>

