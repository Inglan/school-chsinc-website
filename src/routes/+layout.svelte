<script lang="ts">
  import "../app.css";
  import { ModeWatcher } from "mode-watcher";
  import { Header } from "$lib/components/custom/header/index.js";
</script>

<ModeWatcher />
<div class="flex min-h-screen w-full flex-col">
  <Header />

  <slot></slot>
</div>
