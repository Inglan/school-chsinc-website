<script lang="ts">
  import CircleUser from "lucide-svelte/icons/circle-user";
  import Menu from "lucide-svelte/icons/menu";
  import Package2 from "lucide-svelte/icons/package-2";
  import Search from "lucide-svelte/icons/search";
  import Sun from "lucide-svelte/icons/sun";
  import Moon from "lucide-svelte/icons/moon";

  import { toggleMode } from "mode-watcher";
  import { Button, Root } from "$lib/components/ui/button/index.js";
  import * as DropdownMenu from "$lib/components/ui/dropdown-menu/index.js";
  import * as Sheet from "$lib/components/ui/sheet/index.js";

  const nav = [
    { name: "Home", href: "/" },
    { name: "Orders", href: "##" },
    { name: "Products", href: "##" },
    { name: "Customers", href: "##" },
    { name: "Analytics", href: "##" },
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
    <Button href="/contact" class="rounded-full">Get a Quote</Button>
    <DropdownMenu.Root>
      <DropdownMenu.Trigger asChild let:builder>
        <Button
          builders={[builder]}
          variant="secondary"
          size="icon"
          class="rounded-full"
        >
          <CircleUser class="h-5 w-5" />
          <span class="sr-only">Toggle user menu</span>
        </Button>
      </DropdownMenu.Trigger>
      <DropdownMenu.Content align="end">
        <DropdownMenu.Label>My Account</DropdownMenu.Label>
        <DropdownMenu.Separator />
        <DropdownMenu.Item>Settings</DropdownMenu.Item>
        <DropdownMenu.Item>Support</DropdownMenu.Item>
        <DropdownMenu.Separator />
        <DropdownMenu.Item>Logout</DropdownMenu.Item>
      </DropdownMenu.Content>
    </DropdownMenu.Root>
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
