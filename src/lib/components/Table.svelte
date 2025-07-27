<script>
	import Card from "./Card.svelte";
	import Chips from "./Chips.svelte";

</script>
<div class="w-10/12 h-5/6 bg-green-800 rounded-tr-2xl rounded-tl-2xl border-l-6 border-r-6 border-t-6 border-black">
    <Chips></Chips>
    <Chips></Chips>
    <Chips></Chips>
    <div class="w-full flex items-center justify-center">
        <div class="w-7/12 flex items-center justify-around">
            <Card></Card>
            <Card></Card>
            <Card></Card>
        </div>
    </div>
</div>