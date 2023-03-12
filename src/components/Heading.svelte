<script>
  export let courseGoal;
  export let isValid;
</script>

<h1 class={isValid == "false" ? "bg-red-500" : ""}>{courseGoal}</h1>
