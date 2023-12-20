<script>
  import Vault from "./Vault.svelte";
  import { getData } from "./data.js";
</script>

<Vault files={getData()} />
