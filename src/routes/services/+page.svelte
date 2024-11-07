<script lang="ts">
  import * as Card from "$lib/components/ui/card/index.js";

  const services = [
    {
      title: "Home Repairs",
      description:
        "Our experienced repair personnel can handle a wide variety of home repair needs, from small fixes to major renovations. We focus on precision and efficiency, ensuring all repairs are completed to the highest standard.",
      examples: [
        "Wall and ceiling repairs",
        "Plumbing and electrical fixes",
        "Flooring and structural adjustments",
      ],
    },
    {
      title: "General Maintenance",
      description:
        "Regular maintenance is key to a well-kept home. Our team provides ongoing maintenance services to prevent issues, keeping your home safe, functional, and beautiful.",
      examples: [
        "Seasonal maintenance checks",
        "Exterior and interior upkeep",
        "Preventative repairs and upgrades",
      ],
    },
    {
      title: "Mobile Quotes",
      description:
        "Our mobile quote officers bring convenience to your doorstep. Equipped with mobile technology, they’ll assess the work needed, answer your questions, and provide an accurate, on-site estimate.",
      examples: [
        "Schedule an on-site visit",
        "Receive a clear, itemized quote",
        "Review and approve the work plan",
      ],
    },
    {
      title: "Custom Repair Solutions",
      description:
        "For unique or more complex repair needs, we offer custom solutions tailored to your property’s requirements. No two homes are the same, and we’re committed to finding the right solution for you.",
    },
  ];
</script>

<svelte:head>
  <title>Services - CHS Inc</title>
</svelte:head>

<div class="relative w-full max-w-6xl h-[800px] max-h-screen mx-auto mb-5">
  <!-- Before Image -->
  <div class="absolute inset-0">
    <enhanced:img
      src="$lib/images/photos/repair.jpg"
      alt="Decorative Background Image"
      class="w-full h-full object-cover brightness-50 rounded-lg"
    />
  </div>
  <!-- Overlay Text -->
  <div class="absolute inset-0 flex flex-col gap-5 items-center justify-center">
    <h1 class="text-white text-6xl text-center">Services</h1>
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
          {#if service.examples}
            <ul class="list-disc list-inside mt-2">
              {#each service.examples as example}
                <li>{example}</li>
              {/each}
            </ul>
          {/if}
        </Card.Content>
      </Card.Root>
    {/each}
  </div>
  <p class="text-center mt-8">
    Our team is dedicated to making the process as smooth and efficient as
    possible, from initial quote to final repair.
  </p>
</div>
