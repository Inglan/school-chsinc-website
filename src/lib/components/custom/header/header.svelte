<script lang="ts">
  import Menu from "lucide-svelte/icons/menu";
  import Package2 from "lucide-svelte/icons/package-2";
  import Sun from "lucide-svelte/icons/sun";
  import Moon from "lucide-svelte/icons/moon";

  import { toggleMode } from "mode-watcher";
  import { Button } from "$lib/components/ui/button/index.js";
  import * as Sheet from "$lib/components/ui/sheet/index.js";
  import * as Drawer from "$lib/components/ui/drawer/index.js";
  import { Input } from "$lib/components/ui/input/index.js";
  import { toast } from "svelte-sonner";
  import { Textarea } from "$lib/components/ui/textarea/index.js";

  const nav = [
    { name: "Home", href: "/" },
    { name: "Contact", href: "/contact" },
    { name: "About", href: "/about" },
    { name: "Services", href: "/services" },
  ];
</script>

<header
  class="bg-background sticky top-0 flex h-16 items-center gap-4 border-b px-4 md:px-6"
>
  <nav
    class="hidden flex-col gap-6 text-lg font-medium md:flex md:flex-row md:items-center md:gap-5 md:text-sm lg:gap-6"
  >
    <a
      href="/"
      class="flex items-center gap-2 text-lg font-semibold md:text-base"
    >
      <Package2 class="h-6 w-6" />
      <span class="sr-only">CHS Inc</span>
    </a>
    {#each nav as { name, href }}
      <a {href} class="text-foreground hover:text-foreground transition-colors">
        {name}
      </a>
    {/each}
  </nav>
  <Sheet.Root>
    <Sheet.Trigger asChild let:builder>
      <Button
        variant="outline"
        size="icon"
        class="shrink-0 md:hidden"
        builders={[builder]}
      >
        <Menu class="h-5 w-5" />
        <span class="sr-only">Toggle navigation menu</span>
      </Button>
    </Sheet.Trigger>
    <Sheet.Content side="left">
      <nav class="grid gap-6 text-lg font-medium">
        <a href="/" class="flex items-center gap-2 text-lg font-semibold">
          <Package2 class="h-6 w-6" />
          <span class="sr-only">CHS Inc</span>
        </a>
        {#each nav as { name, href }}
          <a {href} class="hover:text-foreground"> {name} </a>
        {/each}
      </nav>
    </Sheet.Content>
  </Sheet.Root>
  <div class="flex w-full items-center gap-2 md:ml-auto md:gap-2 lg:gap-2">
    <div class="ml-auto flex-1 sm:flex-initial"></div>
    <!-- <Button href="/contact" class="rounded-full">Get a Quote</Button> -->
    <Drawer.Root>
      <Drawer.Trigger asChild let:builder>
        <Button builders={[builder]} class="rounded-full">Get a Quote</Button>
      </Drawer.Trigger>
      <Drawer.Content>
        <div class="mx-auto w-full max-w-sm">
          <Drawer.Header>
            <Drawer.Title>Get a Quote</Drawer.Title>
          </Drawer.Header>
          <div class="p-4 pb-0">
            <form class="space-y-4">
              <div>
                <Input
                  id="name"
                  type="text"
                  required
                  class="mt-1 block w-full"
                  placeholder="Name"
                />
              </div>
              <div>
                <Input
                  id="email"
                  type="email"
                  required
                  class="mt-1 block w-full"
                  placeholder="Email"
                />
              </div>
              <div>
                <Input
                  id="phone"
                  type="tel"
                  required
                  class="mt-1 block w-full"
                  placeholder="Phone"
                />
              </div>
              <div>
                <Input
                  id="address"
                  type="text"
                  required
                  class="mt-1 block w-full"
                  placeholder="Address"
                />
              </div>
              <div>
                <Textarea
                  id="repairs"
                  required
                  class="mt-1 block w-full"
                  placeholder="Repairs needed"
                />
              </div>
              <div>
                <Textarea
                  id="comments"
                  required
                  class="mt-1 block w-full"
                  placeholder="Comments"
                />
              </div>
            </form>
          </div>
          <Drawer.Footer>
            <Drawer.Close asChild let:builder>
              <Button
                builders={[builder]}
                on:click={() => {
                  toast.success("Request submitted", {
                    description: "We will contact you soon",
                  });
                }}>Submit</Button
              >
            </Drawer.Close>
            <Drawer.Close asChild let:builder>
              <Button builders={[builder]} variant="outline">Cancel</Button>
            </Drawer.Close>
          </Drawer.Footer>
        </div>
      </Drawer.Content>
    </Drawer.Root>
    <Button
      on:click={toggleMode}
      variant="secondary"
      size="icon"
      class="rounded-full"
    >
      <Sun
        class="h-[1.2rem] w-[1.2rem] rotate-0 scale-100 transition-all dark:-rotate-90 dark:scale-0"
      />
      <Moon
        class="absolute h-[1.2rem] w-[1.2rem] rotate-90 scale-0 transition-all dark:rotate-0 dark:scale-100"
      />
      <span class="sr-only">Toggle theme</span>
    </Button>
  </div>
</header>
