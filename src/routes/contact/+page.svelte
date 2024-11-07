<script lang="ts">
  import { Input } from "$lib/components/ui/input";
  import { Label } from "$lib/components/ui/label";
  import { Textarea } from "$lib/components/ui/textarea";
  import { Button } from "$lib/components/ui/button";
</script>

<svelte:head>
  <title>Contact - CHS Inc</title>
  <meta
    name="description"
    content="Contact CHS Inc for home repair and maintenance services. Get a quote, ask a question, or schedule a service appointment."
  />
</svelte:head>

<div class="relative w-full max-w-6xl h-[800px] max-h-screen mx-auto mb-5">
  <!-- Before Image -->
  <div class="absolute inset-0">
    <enhanced:img
      src="$lib/images/photos/contact.jpg"
      alt="Decorative Background Image"
      class="w-full h-full object-cover brightness-50 rounded-lg"
    />
  </div>
  <!-- Overlay Text -->
  <div class="absolute inset-0 flex flex-col gap-5 items-center justify-center">
    <h1 class="text-white text-6xl text-center">Contact Us</h1>
  </div>
</div>

<div class="relative w-full max-w-6xl mx-auto mb-5">
  <form
    class="space-y-6 max-w-2xl mx-auto"
    on:submit={function (e) {
      e.preventDefault();
      window.open(
        "https://www.youtube.com/watch?v=dQw4w9WgXcQ",
        "",
        "width=400,height=400"
      );
    }}
  >
    <div class="flex flex-col space-y-1.5">
      <Label for="name">Name</Label>
      <Input id="name" type="text" placeholder="Your Name" />
    </div>
    <div class="flex flex-col space-y-1.5">
      <Label for="email">Email</Label>
      <Input id="email" type="email" placeholder="Your Email" />
    </div>
    <div class="flex flex-col space-y-1.5">
      <Label for="message">Message</Label>
      <Textarea id="message" placeholder="Your Message" />
    </div>
    <div class="text-center">
      <Button type="submit">Submit</Button>
    </div>
  </form>
  <br />
  <p class="text-center">Or email us at contact@chsinc.au</p>
</div>
