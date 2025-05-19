<script>
    import { goto } from "$app/navigation";

    const menu_add = () => {
        goto("/menu_add")
    }
</script>

<div>
    <h1>메뉴 추천</h1>
    <button on:click={menu_add}>메뉴 추가</button>
</div>