<script lang="ts">
    import TwoLine from '../assets/TwoLine.svg'
    import Dice from '../assets/Dice.svg'
    import axios from 'axios'


    let id = "117";
    let advice = "“It is easy to sit up and take notice, what's difficult is getting up and taking action.”";

    const handleClick = async () => {
        const response = await axios.get('https://api.adviceslip.com/advice')
        const data = await response.data
        advice = data.slip.advice
        id = data.slip.id
}


</script>
<div class="bg-darkGrayishBlue pt-10 md:pt-12 px-6 md:px-12 w-[343px] md:w-[540px] rounded-[10px] relative md:h-[332px]">
    <div class="flex flex-col items-center gap-y-6 mb-6 md:mb-10">
        {#if advice}
        <p class="text-neonGreen text-[11px] md:text-[13px] font-extrabold tracking-[3.4px] md:tracking-[4px] uppercase">{`ADVICE #${id}`}</p>
        <h1 class="text-lightCyan text-2xl md:text-[28px] md:w-[444px] font-extrabold text-center md:tracking-[-0.3px] md:leading-10">{advice}</h1>
        {/if}
    </div>

    <div class="flex flex-row justify-between items-center mb-[54px]">
        <hr class="w-[122px] md:w-[196px]" />
        <img src={TwoLine} alt="TwoLine" />
        <hr class="w-[122px] md:w-[196px]" />
      </div>
            <!--  -->
    <dir class="absolute -bottom-[40px] md:-bottom-[37px] right-[140px] md:right-[235px] mt-7 m-0 p-0 ">
        <button on:click={handleClick}>
            <img src={Dice} alt="" class="cursor-pointer">
        </button>
    </dir>
</div>