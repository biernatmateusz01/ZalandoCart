<template>
    <div class="mt-2">
        <span class="text-sm font-semibold text-red">{{price}} zł</span>
    </div>
</template>

<script>
export default {
    props: {
        price: String,
    },
};
</script>