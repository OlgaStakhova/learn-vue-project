<template>
<div class="container" >
    <slot></slot>
</div>
    
</template>

<script>
export default {
name: 'ContainerPage',
}
</script>

<style lang="scss">
.container {
 max-width: 1100px;
 display: flex;
flex-wrap: wrap;
}
</style>