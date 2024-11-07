<script lang="ts">
  import "../app.css";
  import { ModeWatcher } from "mode-watcher";
  import { Header } from "$lib/components/custom/header/index.js";
  import { Toaster } from "$lib/components/ui/sonner";

  import { onNavigate } from "$app/navigation";

  onNavigate((navigation) => {
    if (!document.startViewTransition) return;

    return new Promise((resolve) => {
      document.startViewTransition(async () => {
        resolve();
        await navigation.complete;
      });
    });
  });
</script>

<ModeWatcher />
<Toaster />

<div data-vaul-drawer-wrapper="">
  <div class="flex min-h-screen w-full flex-col">
    <Header />

    <div class="p-3">
      <slot></slot>
    </div>

    <footer class="bg-gray-800 text-white text-center py-3">
      <p>&copy; 2025 CHS Inc.</p>
      <p>This is not a real company please dont sue me</p>
    </footer>
  </div>
</div>
