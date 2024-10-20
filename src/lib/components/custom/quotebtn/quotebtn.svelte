<script lang="ts">
  import { Button } from "$lib/components/ui/button/index.js";
  import * as Drawer from "$lib/components/ui/drawer/index.js";
  import { Input } from "$lib/components/ui/input/index.js";
  import { toast } from "svelte-sonner";
  import { Textarea } from "$lib/components/ui/textarea/index.js";
</script>

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
