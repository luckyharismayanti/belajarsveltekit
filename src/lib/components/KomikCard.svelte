<script>
    /**@type string*/
    export let image
    /**@type string*/
    export let title

</script>
<div>
    

    <img
    src={image}
    alt={title}
    />

    <p>{title}</p>
</div>

<style>
    div {
        position: relative;
        height: 100%;
    }
    img {
        height: 100%;
        width: 100%;
        object-fit: cover;
    }
</style>