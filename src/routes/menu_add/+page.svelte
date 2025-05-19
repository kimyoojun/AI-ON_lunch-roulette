<script lang="ts">
    import { goto } from "$app/navigation";
    import { supabase } from "$lib/supabase";
    import {uuid} from "@supabase/supabase-js/dist/main/lib/helpers";
    import { text } from "@sveltejs/kit";

    let menu: String

    const add = async () => {
        const {error: addError} = await supabase
            .from("lunch_menus")
            .insert({
                id:uuid(),
                menu:menu,
            })
        // console.error는 에러를 콘솔에 출력해주는 함수
        if (addError) return console.error
        
        // 에러가 안뜨면 바로 goto실행
        goto("/")
    }
</script>

<div>
    <h1>메뉴 추가</h1>

    <!-- bind:valude={menu}는 menu라는 변수에 input으로 입력한 값을 집어넣는 함수 -->
    <input placeholder="추가할 메뉴를 입력해주세요." bind:value={menu}/>
    <button on:click={add}>추가하기</button>
</div>