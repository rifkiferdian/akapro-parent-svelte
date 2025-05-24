<script>
    import { onMount } from 'svelte';

    const scripts = [
        '/assets/libs/jquery/jquery.min.js',
        '/assets/libs/bootstrap/js/bootstrap.bundle.min.js',
        '/assets/libs/metismenu/metisMenu.min.js',
        '/assets/libs/simplebar/simplebar.min.js',
        '/assets/libs/node-waves/waves.min.js',
        '/assets/js/app.js'
    ];

    onMount(() => {
        // Load scripts sequentially
        const loadScripts = async () => {
            for (const src of scripts) {
                await new Promise((resolve, reject) => {
                    const script = document.createElement('script');
                    script.src = src;
                    script.onload = resolve;
                    script.onerror = reject;
                    document.body.appendChild(script);
                });
            }

        };

        loadScripts().catch(console.error);
    });
</script>

<h1>
    layout paling atas
</h1>
<svelte:head>
    <link href="/assets/css/bootstrap.min.css" id="bootstrap-style" rel="stylesheet" type="text/css" />
    <link href="/assets/css/icons.min.css" rel="stylesheet" type="text/css" />
    <link href="/assets/css/app.min.css" id="app-style" rel="stylesheet" type="text/css" />
</svelte:head>

<main>
    <slot />
</main>