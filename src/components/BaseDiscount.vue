<template>
    <div class="absolute z-50 flex items-center justify-center px-6 py-2 bg-gray-400 top-2">
        <span class="text-sm text-white">{{discountCode}}</span>
    </div>
</template>


<script>
export default {
    props: {
        discountCode: String,
    },
};
</script>