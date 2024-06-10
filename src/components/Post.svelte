
<script>
    import * as Select from "$lib/components/ui/select";

    const types = [
    { value: "popular", label: "Popular" },
    { value: "recent", label: "Recent" },
    { value: "worst", label: "Worst" },
    // { value: "grapes", label: "Grapes" },
    // { value: "pineapple", label: "Pineapple" }
  ];
</script>


<div class="mt-10 w-[50vw]">
    <div class=" pl-4 flex">
        <div class=" mr-3 text-lg font-bold">
            Theory :

        </div> 
        <div class=" bg-white text-black px-2 text-lg font-bold">
            [ Trump a reptlian ? ]

        </div>
        <div class=" border-2 border-gray-500 px-5">
            1.2k

        </div>
    </div>
    <div class="  border-2 border-gray-500 rounded-md">
        <div class=" absolute my-[-15px] mx-[1400px] bg-black px-1">concept(1223)</div>
        <div class="p-4  text-base">
            During one of the press conference trumps eyes blinked like a reptile Lorem ipsum dolor sit amet, consectetur adipisicing elit. Esse architecto alias ad dolore quidem! Harum culpa nihil dolores, neque, necessitatibus fugiat minus quam nam laudantium temporibus illo aut, repudiandae id.
        </div>
        <div class="px-4 text-base py-2 align-middle prespective_block flex m-auto">
            
            <div class=" "> <pre>perception : </pre></div> 
                <Select.Root portal={null} class=" translate-y-1">
                            <Select.Trigger class="w-[150px] h-5 translate-y-1">
                                <Select.Value placeholder="Select a type" class="text-gray-500 w-100"/>
                            </Select.Trigger>
                            <Select.Content>
                                <Select.Group>
                                    {#each types as type}
                                    <Select.Item  value={type.value} label={type.label}
                                        >{type.label}</Select.Item
                                    >
                                    {/each}
                                </Select.Group>
                            </Select.Content>
                            <Select.Input name="favoritetype" />
                         </Select.Root> <div class=" "> <pre> : </pre> </div> 
                         <div class=" ml-2 border-2 border-gray-500 px-2 rounded-lg  py-1 text-xs">AHHH yes only that can explain his hair!</div>
        </div>
    </div>
</div>

 



<style>

    .prespective_block {
        background-color: #1e1e1e;

    }
    
</style>