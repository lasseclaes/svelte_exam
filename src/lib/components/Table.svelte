<script>
  import { examorders } from '$lib/examorders';
  // import { createEventDispatcher } from 'svelte';
  import {count_using_stores} from '$lib/stores.js' ;
  export let filter;
  export let tabindex;

  console.log("tabindex " + tabindex);
  console.log("filter: " + filter);


  let oneCat = [];
 
  if (filter !== 'alle'){
  oneCat = examorders.filter(oneorder => oneorder.status === filter);
  }
  else{
    oneCat = examorders;
  }
  //  console.log("length: " + oneCat.length);
  
  let catCount = oneCat.length;

  $count_using_stores[tabindex] = catCount;


  function updateData(e){
    alert("update DB");
    // console.log(e);
  }

  // console.log(oneCat);
</script>
{#if catCount}
<table class="table table-striped" data-lacjbs={filter}>
  <thead>
    <tr>
      <th scope="col">Ordrenr</th>
      <th scope="col">Prøveforekomst</th>
      <th scope="col">Eksamensdato</th>
      <th scope="col">Eksamensnavn</th>
      <th scope="col">Format</th>
      <th scope="col">Type</th>
      <th scope="col">Itemid</th>
      <th scope="col">Status</th>
      <th scope="col">Att</th>
    </tr>
  </thead>
  <tbody>
    {#each oneCat as order}
      <!-- {(console.log(oneCat), '')} -->
      <tr class="align-baseline">
        <th scrope="row">{order.ordernr}</th>
        <td scrope="row">{order.examcode}</td>
        <td scrope="row">{order.examdate}</td>
        <td scrope="row">{order.examname}</td>
        <td scrope="row">{order.docformat}</td>
        <td scrope="row">{order.visionimpaired_exam ? 'Syns' : 'Ordb.'}</td>
        <td scrope="row">{order.itemid}</td>
        <td scrope="row">
          <form on:submit|preventDefault={updateData}>
            <input type="hidden" name="orderid" 
            value="{order.ordernr}">
            <select class="form-select" aria-label="Vælg status" on:change={updateData}>
                <option selected={order.status === "ubehandlede"} value="ubehandlede">Ubehandlet</option>
                <option selected={order.status === "godkendte"} value="godkendte">Godkendt</option>
                <option selected={order.status === "dialog"} value="dialog">Dialog</option>
                <option selected={order.status === "korrektur"} value="korrektur">Korrektur</option>
            </select>

        </form></td> <!-- /* {order.status}*/ -->
        <td scrope="row">
          <form method="post">
           <input type="hidden" name="orderid" 
            value="{order.ordernr}">
            <input type="text" name="att" 
            value="{order.att}">
          </form>
        </td>
      </tr>
    {/each}
  </tbody>
</table>
{:else}
  <p class="mt-4">Nothing here</p>
{/if}
    
<!-- 
<table class="table table-striped">
  <thead>
    <tr>
      <th scope="col">#</th>
      <th scope="col">First</th>
      <th scope="col">Last</th>
      <th scope="col">Handle</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th scope="row">1</th>
      <td>Mark</td>
      <td>Otto</td>
      <td>@mdo</td>
    </tr>
    <tr>
      <th scope="row">2</th>
      <td>Jacob</td>
      <td>Thornton</td>
      <td>@fat</td>
    </tr>
    <tr>
      <th scope="row">3</th>
      <td>Larry</td>
      <td>the Bird</td>
      <td>@twitter</td>
    </tr>
  </tbody>
</table> -->