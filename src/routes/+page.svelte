<script>
  import { tweened } from "svelte/motion";
  import { cubicOut } from "svelte/easing";
  import { onMount } from "svelte";

  let sliderValue = tweened(100, { duration: 1000, easing: cubicOut });

  onMount(() => {
    setTimeout(() => {
      sliderValue.set(0); // Start the animation after 2 seconds
    }, 1000); // 2-second delay
  });
</script>

<div class="relative w-full max-w-6xl h-[800px] max-h-screen mx-auto m-5">
  <!-- Before Image -->
  <div class="absolute inset-0">
    <enhanced:img
      src="$lib/images/photos/hero/before.png"
      alt="Before Image"
      class="w-full h-full object-cover brightness-50 rounded-lg"
    />
  </div>

  <!-- After Image -->
  <div
    class="absolute inset-0"
    style="clip-path: inset(0 0 0 {$sliderValue}%);"
  >
    <enhanced:img
      src="$lib/images/photos/hero/after.png"
      alt="After Image"
      class="w-full h-full object-cover brightness-50 rounded-lg"
    />
  </div>

  <!-- Overlay Text -->
  <div class="absolute inset-0 flex items-center justify-center">
    <h1 class="text-white text-6xl text-center">Home repairs, made easy</h1>
  </div>
</div>
