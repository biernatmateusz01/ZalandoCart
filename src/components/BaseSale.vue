<template>
    <div class="absolute z-50 flex items-center justify-center px-4 py-2 mt-8 bg-red bottom-3">
        <span class="text-xs font-semibold text-white">-{{sale}} %</span>
    </div>
</template>

<script>
export default {
    props: {
        sale: String,
    },
};
</script>