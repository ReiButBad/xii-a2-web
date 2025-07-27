<script lang="ts">
    import Chips from "$lib/components/Chips.svelte";
    import Table from "$lib/components/Table.svelte";
    import { onMount } from "svelte";
    import { slide } from "svelte/transition";

    let selectionScreen: HTMLElement;
    let splashScreen: HTMLElement;
    let triggered = false;
    let showTable = $state(false);
    let touchStartY = 0;


    const sleep = (ms: number) => new Promise((r) => setTimeout(r, ms));

    onMount(() => {

        let hasScrolled = false;

        const playTransition = async () => {
            const container = document.querySelector("#falling-chips-container") as HTMLDivElement;
            splashScreen.classList.add("-translate-y-full")
            container.classList.remove("-translate-y-full");
            await sleep(1500)
            container.style.scale = "10"
            container.style.opacity = "0"
            showTable = true
            await sleep(1000)
            container.remove();
            console.info("transition complete")
            container.remove()
            splashScreen.remove()
            console.info("effects removed from DOM")
        }

        const onTouchStart = (e: TouchEvent) => {
		    touchStartY = e.touches[0].clientY;
        };

        const onTouchMove = (e: TouchEvent) => {
            if (hasScrolled) return;

            const currentY = e.touches[0].clientY;
            const diff = touchStartY - currentY;

            if (diff > 10) {
                hasScrolled = true;
                window.removeEventListener("wheel", onScroll)
                window.removeEventListener("touchstart", onTouchStart)
                window.removeEventListener("touchmove", onTouchMove)
                playTransition()
            }
        };

        const onScroll = (e: WheelEvent) => {
            if(!hasScrolled && e.deltaY > 0) {
                hasScrolled = true;
                window.removeEventListener("wheel", onScroll)
                window.removeEventListener("touchstart", onTouchStart)
                window.removeEventListener("touchmove", onTouchMove)
                playTransition()
            }
        }

        window.addEventListener("wheel", onScroll)
        window.addEventListener("touchstart", onTouchMove)
        window.addEventListener("touchmove", onTouchMove)
    })
</script>

<div id="falling-chips-container" class="w-full h-dvh z-50 fixed pointer-events-none -translate-y-full transition-all duration-[1500ms]">
    <div class="w-full h-full flex items-center justify-around">
        <Chips></Chips>
        <Chips></Chips>
        <Chips></Chips>
    </div>
</div>

<div class="w-full h-dvh z-[49] fixed transition-all duration-1000 {!showTable ? 'translate-y-full' : ''}">
    <div class="w-full h-full flex items-end justify-center">
        <Table></Table>
    </div>
</div>


<div bind:this={splashScreen} class="w-full h-dvh z-40 fixed top-0 left-0 flex justify-center items-center transition-all duration-1000 bg-gradient-to-b from-70% from-zinc-950 to-transparent">
    <section class="w-3/4 h-20 flex items-center justify-center">
        <span id="splash" class="font-retrosigned text-white text-9xl">
            <span>X</span>
            <span>I</span>
            <span>I</span>
            <span></span>
            <span></span>
            <span class="text-pink-300 text-shadow-pink-300" style="text-shadow: 0 0 20px">A</span>
            <span>2</span>
            
        </span>
    </section>
</div>

<div bind:this={selectionScreen} class="w-full h-dvh bg-zinc-950 flex justify-center items-center">
    <section class="w-3/4 flex items-center justify-center">
        <span id="wip" class="font-lasenter text-white text-9xl text-center">Work In Progress</span>
    </section>
</div>


<style>

    @font-face {
        font-family: "RetroSigned";
        src: url("/RetroSigned-DYYY0.ttf")
    }

    @font-face {
        font-family: "LasEnter";
        src: url("/LasEnterPersonalUseOnly-D301.ttf")
    }

    .font-lasenter {
        font-family: "LasEnter";
    }

    .font-retrosigned {
        font-family: "RetroSigned";
    }

    #splash span {
        display: inline-block;
        animation: bounce 2s infinite ease-in-out;
    }

    #splash span:nth-child(1) {
        animation-delay: 0s;
    }
    #splash span:nth-child(2) {
        animation-delay: 0.1s;
    }
    #splash span:nth-child(3) {
        animation-delay: 0.2s;
    }
    #splash span:nth-child(6) {
        animation-delay: 0.3s;
    }
    #splash span:nth-child(7) {
        animation-delay: 0.4s;
    }

    #wip {
        animation: neon 5s infinite ease-in-out;
    }

    @keyframes bounce {
        0%,
        100% {
            transform: translateY(0);
        }
        50% {
            transform: translateY(10px);
        }
    }

    @keyframes neon {
        0%, 100% {
            color: var(--color-pink-300);
            text-shadow: 0 0 20px var(--color-pink-300);
        }
        50% {
            color: var(--color-pink-900);
            text-shadow: 0 0 2px var(--color-pink-600);
        }
    }

</style>