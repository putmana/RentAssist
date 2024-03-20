<script lang="ts">
  import Textbox from "./lib/textbox/textbox.svelte";

  function calcRent(
    base: number,
    addon: number,
    count: number,
    percent: number,
  ) {
    percent = percent / 100;
    console.log(percent);
    console.log(count);
    console.log(addon);
    return Math.ceil(base * percent + addon / count);
  }

  let base: number = 1700;
  let mdu: number = 50;
  let nwe: number = 250;
  let internet: number = 100;
  let misc: number = 0;

  let addon: number = 0;

  $: addon = mdu + nwe + internet + misc;

  let renters_count = 5;

  let renters = {
    brandon: 31,
    adam: 23,
    alex: 23,
    peyton: 23,
  };
</script>

<main>
  <div class="values">
    <Textbox label="Base Rent" id="base" type="number" bind:value={base} />
    <Textbox label="MDU" id="mdu" type="number" bind:value={mdu} />
    <Textbox label="NWE" id="nwe" type="number" bind:value={nwe} />
    <Textbox label="ISP" id="internet" type="number" bind:value={internet} />
    <Textbox label="Misc" id="misc" type="number" bind:value={misc} />
  </div>

  <table>
    <tr>
      <td class="name">Brandon</td>
      <td class="amount"
        >${calcRent(base, addon, renters_count, renters.brandon)}</td
      >
    </tr>
    <tr>
      <td class="name">Adam</td>
      <td class="amount"
        >${calcRent(base, addon, renters_count, renters.adam)}</td
      >
    </tr>
    <tr>
      <td class="name">Alex</td>
      <td class="amount"
        >${calcRent(base, addon, renters_count, renters.alex)}</td
      >
    </tr>
    <tr>
      <td class="name">Peyton</td>
      <td class="amount"
        >${calcRent(base, addon, renters_count, renters.peyton)}</td
      >
    </tr>
  </table>
</main>

<style lang="scss">
  @use "/src/lib/vars";
  @use "/src/lib/colors";

  :global(body) {
    background-color: colors.$background_c;
    font-size: 16px;
    font-family:
      system-ui,
      -apple-system,
      BlinkMacSystemFont,
      "Segoe UI",
      Roboto,
      Oxygen,
      Ubuntu,
      Cantarell,
      "Open Sans",
      "Helvetica Neue",
      sans-serif;
  }

  main {
    display: flex;
    flex-direction: column;
    gap: vars.$form_gap;
  }

  .values {
    display: flex;
    flex-direction: column;
    gap: vars.$form_gap;
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
