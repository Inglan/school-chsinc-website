<script lang="ts">
  import Menu from "lucide-svelte/icons/menu";
  import Sun from "lucide-svelte/icons/sun";
  import Moon from "lucide-svelte/icons/moon";

  import { toggleMode } from "mode-watcher";
  import { Button } from "$lib/components/ui/button/index.js";
  import * as Sheet from "$lib/components/ui/sheet/index.js";
  import * as Drawer from "$lib/components/ui/drawer/index.js";
  import { Input } from "$lib/components/ui/input/index.js";
  import { toast } from "svelte-sonner";
  import { Textarea } from "$lib/components/ui/textarea/index.js";
  import { Quotebtn } from "$lib/components/custom/quotebtn/index.js";

  const nav = [
    { name: "Home", href: "/" },
    { name: "Contact", href: "/contact" },
    { name: "About", href: "/about" },
    { name: "Services", href: "/services" },
  ];
</script>

<header
  class="z-50 bg-background sticky top-0 flex h-16 items-center gap-4 border-b px-4 md:px-6"
>
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
        {#each nav as { name, href }}
          <a {href} class="hover:text-foreground"> {name} </a>
        {/each}
      </nav>
    </Sheet.Content>
  </Sheet.Root>
  <nav
    class="flex-col gap-6 text-lg font-medium md:flex md:flex-row md:items-center md:gap-5 md:text-sm lg:gap-6"
  >
    <a
      href="/"
      class="flex items-center gap-2 text-lg font-semibold md:text-base h-8 w-8"
    >
      <enhanced:img src="$lib/images/logo.png" class="h-8 w-8" />
      <span class="sr-only">CHS Inc</span>
    </a>
    <div class="flex flex-row gap-3 hidden md:flex">
      {#each nav as { name, href }}
        <a
          {href}
          class="text-foreground hover:text-foreground transition-colors text-base"
        >
          {name}
        </a>
      {/each}
    </div>
  </nav>
  <div class="flex w-full items-center gap-2 md:ml-auto md:gap-2 lg:gap-2">
    <div class="ml-auto flex-1 sm:flex-initial"></div>
    <Quotebtn />
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
