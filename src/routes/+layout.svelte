<script>
  import "../app.css";
  import { ModeWatcher } from "mode-watcher";
</script>

<ModeWatcher />
<div class="flex min-h-screen w-full flex-col">
  <slot></slot>
</div>
