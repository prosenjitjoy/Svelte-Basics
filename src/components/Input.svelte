<script>
  import Heading from "./Heading.svelte";
  let courseGoal;
  $: isValid = courseGoal?.match(/!/g) ? "false" : "true";
</script>

<div class="container p-5">
  <label for="goal">Course Goal</label>
  <input
    id="goal"
    type="text"
    class="block rounded-md border border-gray-300 bg-gray-50 p-2.5 text-sm text-gray-900"
    bind:value={courseGoal}
  />
  <Heading {courseGoal} {isValid} />
</div>
