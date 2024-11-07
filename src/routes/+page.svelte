<script lang="ts">
  import { Button } from "$lib/components/ui/button/index.js";

  import { tweened } from "svelte/motion";
  import { cubicOut } from "svelte/easing";
  import { onMount } from "svelte";
  import { Quotebtn } from "$lib/components/custom/quotebtn/index.js";

  import Star from "svelte-material-icons/Star.svelte";

  let sliderValue = tweened(100, { duration: 1000, easing: cubicOut });
  import * as Card from "$lib/components/ui/card/index.js";

  const services = [
    {
      title: "Home Repairs",
      description:
        "Whether it's a small fix or a major restoration, our experienced repair personnel handle all types of home repairs with precision and care.",
    },
    {
      title: "General Maintenance",
      description:
        "We offer ongoing maintenance services to ensure your home remains in excellent condition year-round, preventing issues before they become costly problems.",
    },
    {
      title: "Mobile Quotes",
      description:
        "Our quote officers come directly to your home, equipped with the latest mobile technology to assess the work needed and provide fast, accurate estimates.",
    },
    {
      title: "Custom Solutions",
      description:
        "No two homes are the same, so we provide personalized repair plans based on your specific requirements.",
    },
  ];

  const reasons = [
    {
      title: "Experienced Professionals",
      description:
        "Our skilled repair personnel and dedicated quote officers bring years of expertise to every job, ensuring top-notch results.",
    },
    {
      title: "Customer-First Approach",
      description:
        "We value open communication and are committed to delivering service that meets your needs and budget.",
    },
    {
      title: "Transparent Quotes",
      description:
        "No hidden fees—our quotes are clear, detailed, and provided on-site for your convenience.",
    },
    {
      title: "Reliability & Accountability",
      description:
        "We show up on time, respect your space, and complete every job with professionalism and care.",
    },
  ];

  const reviews = [
    {
      title: "Rick Asstley",
      description:
        "I was impressed with the level of service and attention to detail CHS Incorporated provided. They went above and beyond to ensure my repairs were completed to my satisfaction.",
    },
    {
      title: "Tim Cock",
      description:
        "I've used CHS Incorporated for multiple home repairs and have been consistently impressed with the quality of their work. They are my go-to for all my repair needs.",
    },
    {
      title: "Sam Sung",
      description:
        "CHS Incorporated is the best in the business. They are reliable, professional, and always deliver exceptional results. I wouldn't trust anyone else with my home repairs.",
    },
    {
      title:
        "Dr. Octavius Thaddeus Sinclair the 69th, Lord Protector of the Commonwealth, Knight of the Sapphire Order, Ph.D., M.Sc., Fellow of the Royal Astronomical Society",
      description:
        "CHS Incorporated made my home repairs a breeze. The team was professional, efficient, and the results were outstanding. Highly recommend!",
    },
  ];

  onMount(() => {
    setTimeout(() => {
      sliderValue.set(0); // Start the animation after 2 seconds
    }, 1000); // 2-second delay
  });
</script>

<div class="relative w-full max-w-6xl h-[800px] max-h-screen mx-auto mb-5">
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
    <h1 class="text-white text-6xl text-center px-2">
      Reliable Home Repairs, Made Easy
    </h1>
    <p class="text-white text-center px-2">
      Expert quotes and quality repairs delivered to your door.
    </p>
    <div class="flex flex-row gap-2">
      <Quotebtn />
      <Button href="/contact" class="rounded-full" variant="secondary"
        >Contact</Button
      >
    </div>
  </div>
</div>

<div class="relative w-full max-w-6xl mx-auto mb-5">
  <h2 class="text-4xl text-center mb-4">Our Services</h2>
  <p class="text-center mb-8">
    At CHS Incorporated, we provide a comprehensive range of home repair and
    maintenance services, tailored to meet your needs:
  </p>
  <div class="grid grid-cols-1 md:grid-cols-2 gap-6">
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
  <p class="text-center mt-8">
    Our team is dedicated to making the process as smooth and efficient as
    possible, from initial quote to final repair.
  </p>
</div>
<div class="relative w-full max-w-6xl h-[800px] max-h-screen mx-auto mb-5">
  <div class="absolute inset-0">
    <enhanced:img
      src="$lib/images/photos/drill.jpg"
      alt="Decorative repair image"
      class="w-full h-full object-cover rounded-lg"
    />
  </div>
</div>

<div class="relative w-full max-w-6xl mx-auto mb-5">
  <h2 class="text-4xl text-center mb-4">Why Choose CHS Incorporated?</h2>
  <p class="text-center mb-8">
    At CHS Incorporated, we go beyond basic repairs. Here's why homeowners trust
    us with their properties:
  </p>
  <div class="grid grid-cols-1 md:grid-cols-2 gap-6">
    {#each reasons as reason}
      <Card.Root class="rounded-lg">
        <Card.Header>
          <Card.Title>{reason.title}</Card.Title>
        </Card.Header>
        <Card.Content>
          <p>{reason.description}</p>
        </Card.Content>
      </Card.Root>
    {/each}
  </div>
</div>
<div class="relative w-full max-w-6xl h-[800px] max-h-screen mx-auto mb-5">
  <div class="absolute inset-0">
    <enhanced:img
      src="$lib/images/photos/painting.jpg"
      alt="Repair decorative image"
      class="w-full h-full object-cover rounded-lg"
    />
  </div>
</div>

<div class="relative w-full max-w-6xl mx-auto mb-5">
  <h2 class="text-4xl text-center mb-4">Reviews</h2>
  <p class="text-center mb-8">
    Here are some legit completley real balanced reviews from our satisfied
    customers.
  </p>
  <div class="grid grid-cols-1 md:grid-cols-2 gap-6">
    {#each reviews as review}
      <Card.Root class="rounded-lg">
        <Card.Header>
          <Card.Title>{review.title}</Card.Title>
          <div class="flex flex-row gap-1">
            <Star />
            <Star />
            <Star />
            <Star />
            <Star />
          </div>
        </Card.Header>
        <Card.Content>
          <p>{review.description}</p>
        </Card.Content>
      </Card.Root>
    {/each}
  </div>
</div>

<div class="relative w-full max-w-6xl h-[800px] max-h-screen mx-auto mb-5">
  <div class="absolute inset-0">
    <enhanced:img
      src="$lib/images/photos/house.jpg"
      alt="Nice house"
      class="w-full h-full object-cover rounded-lg"
    />
  </div>
</div>

<div class="relative w-full max-w-6xl mx-auto mb-5">
  <h2 class="text-4xl text-center mb-4">The Choice is Clear</h2>
  <div class="flex items-center justify-center">
    <Quotebtn />
  </div>
</div>
