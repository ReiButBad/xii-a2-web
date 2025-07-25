<div class="w-full h-dvh p-0 m-0">
    <div class="p-0 m-0 w-full h-dvh flex justify-center items-center">
        <div class="w-3/4 h-20 flex items-center justify-center">
            <h1 id="splash" class="font-retrosigned text-white text-9xl">
                <span>X</span>
                <span>I</span>
                <span>I</span>
                <span></span>
                <span></span>
                <span class="text-pink-300 text-shadow-pink-300" style="text-shadow: 0 0 20px">A</span>
                <span>2</span>
                
            </h1>
        </div>
    </div>
    <div class=" p-0 m-0 w-full h-dvh flex justify-center items-center">
        <div class="w-3/4 h-20 flex items-center justify-center">
            <h1 id="wip" class="font-lasenter text-white text-9xl">Work In Progress</h1>
        </div>
    </div>
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