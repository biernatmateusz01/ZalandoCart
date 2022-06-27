<template>
    <div class="mt-2">
        <p class="w-full text-sm text-black">{{brand}}</p>
        <br/>
        <p class="w-full -mt-6 text-sm text-black truncate">{{productName}}</p>
    </div>
</template>

<script>
export default {
    props: {
        brand: String,
        productName: String,
    },
};
</script>