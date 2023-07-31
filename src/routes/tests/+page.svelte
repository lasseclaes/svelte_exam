<script>
  import { count_using_stores } from "$lib/stores.js";
  import { page } from "$app/stores";
  let countInPage;

  count_using_stores.subscribe((value) => {
    countInPage = value;
  });
</script>

<p>
  Er stores tilgængelige over alt?

  {#each countInPage as one}
    {one},&nbsp;
  {/each}
</p>
<p>
  Hvis man gør direkte ind på store_test tager den default værdierne, medens
  hvis man er omkring bestillinger først så bliver de sat - og man kan tilgå
  dem.
</p>

<div><h5>spacing</h5></div>
<p name="here" id="here">Test deep link: Here</p>
<p>{$page.url.searchParams}</p>

<style>
  h5 {
    background-color: red;
    height: 100vh;
  }
</style>
