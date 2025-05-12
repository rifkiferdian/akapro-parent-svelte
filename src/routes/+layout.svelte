<script>
    const {children} = $props();

    import { onMount } from 'svelte';

    // Untuk script non-kritis yang dimuat di akhir
    onMount(() => {
        function loadScriptSequentially(urls, index = 0) {
            if (index >= urls.length) return;
            
            const script = document.createElement('script');
            script.src = urls[index];
            script.onload = () => loadScriptSequentially(urls, index + 1);
            document.body.appendChild(script);
        }
        
        const nonCriticalScripts = [
        '/assets/libs/metismenu/metisMenu.min.js',
        '/assets/libs/simplebar/simplebar.min.js',
        '/assets/libs/node-waves/waves.min.js',
        '/assets/js/app.js'
        ];
        
        loadScriptSequentially(nonCriticalScripts);
    });
</script>

<svelte:head>
    <link href="/assets/css/bootstrap.min.css" id="bootstrap-style" rel="stylesheet" type="text/css" />
    <link href="/assets/css/icons.min.css" rel="stylesheet" type="text/css" />
    <link href="/assets/css/app.min.css" id="app-style" rel="stylesheet" type="text/css" />

    <!-- Script kritis dengan defer -->
    <script src="/assets/libs/jquery/jquery.min.js" defer></script>
    <script src="/assets/libs/bootstrap/js/bootstrap.bundle.min.js" defer></script>
</svelte:head>

{@render children()}