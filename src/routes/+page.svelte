<script lang="ts">
  import { Button } from "$lib/components/ui/button/index.js";

  import { tweened } from "svelte/motion";
  import { cubicOut } from "svelte/easing";
  import { onMount } from "svelte";
  import { Quotebtn } from "$lib/components/custom/quotebtn/index.js";

  let sliderValue = tweened(100, { duration: 1000, easing: cubicOut });
  import * as Card from "$lib/components/ui/card/index.js";

  const services = [
    {
      title: "Home Repairs",
      description: "From minor fixes to major restorations.",
    },
    {
      title: "General Maintenance",
      description: "Keeping your home in top shape.",
    },
    {
      title: "Mobile Quotes",
      description: "Quick, on-site estimates at your convenience.",
    },
  ];

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
  <div class="absolute inset-0 flex flex-col gap-5 items-center justify-center">
    <h1 class="text-white text-6xl text-center">
      Reliable Home Repairs, Made Easy
    </h1>
    Expert quotes and quality repairs delivered to your door.
    <div class="flex flex-row gap-2">
      <Quotebtn />
      <Button href="/contact" class="rounded-full" variant="secondary"
        >Contact</Button
      >
    </div>
  </div>
</div>

<div class="relative w-full max-w-6xl mx-auto m-5">
  <h2 class="text-4xl text-center mb-8">What We Do</h2>
  <div class="grid grid-cols-1 md:grid-cols-3 gap-6">
    {#each services as service}
      <Card.Root class="rounded-lg">
        <Card.Header>
          <Card.Title>{service.title}</Card.Title>
        </Card.Header>
        <Card.Content>
          <p>{service.description}</p>
        </Card.Content>
      </Card.Root>
    {/each}
  </div>
</div>
