<template>
    <div>
        <header>
            <slot></slot>
            <slot name="header"></slot>
        </header>
        <main>
            <slot name="content"></slot>
        </main>
        <footer>
            <slot name="footer"></slot>
        </footer>
    </div>
</template>

<script>
    export default {
        
    }
</script>