<script lang="ts">

  function calcRent(base: number, addon: number, count: number, percent: number) {
    percent = percent / 100;
    console.log(percent);
    console.log(count);
    console.log(addon)
    return Math.ceil((base * percent) + (addon / count));
  }

  let base: number = 1700;
  let mdu: number = 50;
  let nwe: number = 250;
  let internet: number = 100;
  let misc: number = 0;

  let addon: number = 0;

  $: addon = mdu + nwe + internet + misc;

  let renters_count = 5

  let renters = {
    brandon: 15.5,
    faith: 15.5,
    adam: 23,
    alex: 23,
    peyton: 23
  }
  
</script>

<main>
  <div class="values">
    <label for="base">Base Rent</label>
    <input name="base" type="number" bind:value={base}>

    <label for="base">MDU</label>
    <input name="mdu" type="number" bind:value={mdu}>

    <label for="base">NWE</label>
    <input name="nwe" type="number" bind:value={nwe}>

    <label for="base">Internet</label>
    <input name="internet" type="number" bind:value={internet}>

    <label for="base">Misc</label>
    <input name="misc" type="number" bind:value={misc}>

  </div>
  

  <table>
    <tr>
      <td class="name">Brandon</td>
      <td class="amount">${calcRent(base, addon, renters_count, renters.brandon)}</td>
    </tr>
    <tr>
      <td class="name">Faith</td>
      <td class="amount">${calcRent(base, addon, renters_count, renters.faith)}</td>
    </tr>
    <tr>
      <td class="name">Adam</td>
      <td class="amount">${calcRent(base, addon, renters_count, renters.adam)}</td>
    </tr>
    <tr>
      <td class="name">Alex</td>
      <td class="amount">${calcRent(base, addon, renters_count, renters.alex)}</td>
    </tr>
    <tr>
      <td class="name">Peyton</td>
      <td class="amount">${calcRent(base, addon, renters_count, renters.peyton)}</td>
    </tr>
  </table>
  

</main>


<style lang="scss">
  main {
    font-size: 12pt;
  }
  .values {
    width: 10rem;
    display: flex;
    flex-direction: column;
    margin-bottom: 2rem;
    input {
      padding: 5pt;
      flex-grow: 1;
      margin-bottom: 1rem;
    }
  }
  table {
    width: 100%;
    .name {
      text-align: left;
    }
    .amount {
      text-align: right;
    }
  }
  
  
</style>
