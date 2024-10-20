<script lang="ts">
  import "../app.css";
  import { ModeWatcher } from "mode-watcher";
  import { Header } from "$lib/components/custom/header/index.js";
  import { Toaster } from "$lib/components/ui/sonner";
</script>

<ModeWatcher />
<Toaster />

<div data-vaul-drawer-wrapper="">
  <div class="flex min-h-screen w-full flex-col">
    <Header />

    <slot></slot>
  </div>
</div>
