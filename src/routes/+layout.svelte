<script lang="ts">
    import "../app.pcss";
    import {AppBar, AppLayout, Button, Menu, MenuItem, NavItem, Settings, Toggle} from 'svelte-ux';
    import { page } from "$app/stores";
    import {mdiAccount, mdiFileMultiple, mdiHome} from "@mdi/js";
</script>

<AppLayout>
    <nav slot="nav" class="h-full">
        <NavItem text="Home" icon={mdiHome} currentUrl={$page.url} path="/" />
        <NavItem text="Files" icon={mdiFileMultiple} currentUrl={$page.url} path="/files" />
    </nav>

    <AppBar title="Bungy" class="bg-primary" menuIcon={null}>
        <div slot="actions">
            <Settings classes={{Button: "border-2 font-bold", Menu: "shadow-xl border-gray-500", MenuItem: "font-bold"}}>
                <Toggle let:on={open} let:toggle>
                    <Button on:click={toggle} icon={mdiAccount}>
                        Luke
                        <Menu {open} on:close={toggle}>
                            <MenuItem href="/account">Manage Account</MenuItem>
                        </Menu>
                    </Button>
                </Toggle>
            </Settings>
        </div>
    </AppBar>

    <main>
        <slot />
    </main>
</AppLayout>