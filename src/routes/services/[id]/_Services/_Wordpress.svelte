<script lang="ts">
	import CopyPasswordField from '$lib/components/CopyPasswordField.svelte';

	export let service;
	export let isRunning;
	export let readOnly;
</script>

<div class="flex space-x-1 py-5 font-bold">
	<div class="title">Wordpress</div>
</div>

<div class="grid grid-cols-2 items-center px-10">
	<label for="extraConfig">Extra Config</label>
	<textarea
		disabled={isRunning}
		readonly={isRunning}
		class:resize-none={isRunning}
		rows={isRunning ? 1 : 5}
		name="extraConfig"
		id="extraConfig"
		placeholder={!isRunning
			? `eg:

define('WP_ALLOW_MULTISITE', true);
define('MULTISITE', true);
define('SUBDOMAIN_INSTALL', false);`
			: 'N/A'}>{service.wordpress.extraConfig}</textarea
	>
</div>
<div class="flex space-x-1 py-5 font-bold">
	<div class="title">MySQL</div>
</div>
<div class="grid grid-cols-2 items-center px-10">
	<label for="mysqlDatabase">Database</label>
	<input
		name="mysqlDatabase"
		id="mysqlDatabase"
		required
		readonly={readOnly}
		disabled={readOnly}
		bind:value={service.wordpress.mysqlDatabase}
		placeholder="eg: wordpress_db"
	/>
</div>
<div class="grid grid-cols-2 items-center px-10">
	<label for="mysqlRootUser">Root User</label>
	<input
		name="mysqlRootUser"
		id="mysqlRootUser"
		placeholder="MySQL Root User"
		value={service.wordpress.mysqlRootUser}
		disabled
		readonly
	/>
</div>
<div class="grid grid-cols-2 items-center px-10">
	<label for="mysqlRootUserPassword">Root's Password</label>
	<CopyPasswordField
		id="mysqlRootUserPassword"
		isPasswordField
		readonly
		disabled
		name="mysqlRootUserPassword"
		value={service.wordpress.mysqlRootUserPassword}
	/>
</div>
<div class="grid grid-cols-2 items-center px-10">
	<label for="mysqlUser">User</label>
	<input name="mysqlUser" id="mysqlUser" value={service.wordpress.mysqlUser} disabled readonly />
</div>
<div class="grid grid-cols-2 items-center px-10">
	<label for="mysqlPassword">Password</label>
	<CopyPasswordField
		id="mysqlPassword"
		isPasswordField
		readonly
		disabled
		name="mysqlPassword"
		value={service.wordpress.mysqlPassword}
	/>
</div>
