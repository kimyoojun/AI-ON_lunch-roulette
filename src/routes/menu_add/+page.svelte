<script lang="ts">
    import {supabase} from "$lib/supabase";
    import {uuid} from "@supabase/supabase-js/dist/main/lib/helpers";
    import {goto} from "$app/navigation";

    let menu: string

    const add = async () => {
        const {error: addError} = await supabase
            .from("lunch_menus")
            .insert({
                id: uuid(),
                menu: menu,
            })

        if (addError) return console.error(addError)

        goto("/")

    }
</script>

<div>
    <h1>메뉴 추가</h1>

    <input placeholder="추가할 메뉴를 입력해주세요." bind:value={menu}/>
    <button on:click={add}>추가하기</button>
</div>
