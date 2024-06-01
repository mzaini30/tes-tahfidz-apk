<script>
  import "./css/water.css";
  import { range } from "range";
  import { acak } from "kumpulan-tools";
  import Swal from "sweetalert2";
  import jualan from "./jualan.yaml";

  let juz = [];
  let kumpulanHalaman = [];

  function olah() {
    kumpulanHalaman = [];
    for (let j of juz) {
      let halaman = [];
      for (let n = 2; n <= 21; n++) {
        halaman = [...halaman, (j - 1) * 20 + n];
      }
      kumpulanHalaman = [...kumpulanHalaman, ...halaman];
    }
    let terpilih = acak(kumpulanHalaman)[0];
    Swal.fire({
      title: `Ujian Halaman ${terpilih}`,
    });
  }
</script>

<h1>Tes Tahfidz</h1>

<div class="wadah-juz">
  {#each range(1, 31) as x}
    <label class="pilihan-juz">
      <input bind:group={juz} value={x} type="checkbox" name="" id="" />
      Juz {x}
    </label>
  {/each}
</div>
{#if juz.length > 0}
  <button on:click={olah} class="tombol-tes">Tes</button>
{/if}

<h2>Store</h2>
{#each jualan as item}
  <p class="p-jualan">
    <a href={item.link} class="a-jualan">
      <img src={item.gambar} alt="" class="img-jualan" />
    </a>
  </p>
{/each}

<style>
  .wadah-juz {
    font-size: 25px;
    column-count: 2;
    margin-bottom: 10px;
  }

  label.pilihan-juz {
    display: block;
    user-select: none;
  }

  button.tombol-tes {
    background: green;
    color: white;
    text-transform: uppercase;
  }
</style>
