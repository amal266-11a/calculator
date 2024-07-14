
<script lang="ts">
import { onMount } from "svelte";


let a:string="";
function eqeione (value:string){
a+=value;
}

function blackSpace (){
switch (a.substring(a.length-3,a.length)){
    case "*":
    case "-" :
    case "/":
    case "+":
 a=a.substring(0,a.length-3); 
      break;                 
default:
    a=a.substring(0,a.length-1);
}
}

function deletee (){
 a="" ;  
}
function solve(){
    try {
            a=eval(a);
        } catch (error) {
          alert ('المعادلة غير صالحه') ;
        }
}

function onKeyDown(e:KeyboardEvent){
  document.getElementById(e.key)?.click();  
    
}
onMount(() => {
    let allButtun=document.getElementsByTagName('button');
    for(let i=0;i<allButtun.length;i++){
        allButtun[i].addEventListener('click',() => {
            new Audio('/click.wav').play();
        });
    }
});
</script>

<svelte:head>
    <title>
        اله حاسبة
    </title>
</svelte:head>

<svelte:window on:keydown|preventDefault={onKeyDown} />

<div class=" bg-red-100 h-[23rem] w-[19rem] rounded-3xl grid grid-cols-4 gap-1 p-6 text-xl font-bold shadow-2xl max-w-[17rem]">
    <div class=" bg-red-300 rounded-xl col-span-4 min-h-12 flex items-center pl-3 mb-3 text-white shadow-lg overflow-x-auto">
{a}
    </div>
  <button id="%" on:click={() => eqeione("/100")} class=" bg-slate-100 shadow-lg text-stone-400" >%</button> 
  <button id="Backspace"  on:click={blackSpace} class=" flex items-center justify-center text-stone-400"><svg xmlns="http://www.w3.org/2000/svg" width="1em" height="1em" viewBox="0 0 16 16"><path fill="currentColor" fill-rule="evenodd" d="M5.442 3.5H12.5A1.5 1.5 0 0 1 14 5v6a1.5 1.5 0 0 1-1.5 1.5H5.442a1.5 1.5 0 0 1-1.171-.563L1.796 8.844a1.35 1.35 0 0 1 0-1.688l2.475-3.093A1.5 1.5 0 0 1 5.44 3.5m-2.343-.374A3 3 0 0 1 5.442 2H12.5a3 3 0 0 1 3 3v6a3 3 0 0 1-3 3H5.442a3 3 0 0 1-2.343-1.126L.625 9.781a2.85 2.85 0 0 1 0-3.562zM7.28 5.47a.75.75 0 0 0-1.06 1.06L7.69 8L6.22 9.47a.75.75 0 1 0 1.06 1.06l1.47-1.47l1.47 1.47a.75.75 0 1 0 1.06-1.06L9.81 8l1.47-1.47a.75.75 0 0 0-1.06-1.06L8.75 6.94z" clip-rule="evenodd"/></svg></button>
  <button id="Delete" on:click={deletee} class= " bg-slate-100 text-stone-400 shadow-lg  ">C</button>
  <button id="+" on:click={() => eqeione("+")}  class=" bg-green-100 shadow-lg">+</button>
  
  <button id="7" on:click={() => eqeione("7")} class=" bg-slate-200 shadow-lg text-stone-400"> 7 </button>
  <button id="8" on:click={() => eqeione("8")} class=" bg-slate-200 shadow-lg text-stone-400" >8</button>
  <button id="9" on:click={() => eqeione("9")} class=" bg-slate-200 shadow-lg text-stone-400" >9</button>
  <button id="-" on:click={() => eqeione(" - ")} class=" bg-red-500 shadow-lg">-</button>
  <button id="4" on:click={() => eqeione("4")} class=" bg-slate-200 shadow-lg text-stone-400">4</button>
  <button id="5" on:click={() => eqeione("5")} class=" bg-slate-200 shadow-lg text-stone-400">5</button>
  <button id="6" on:click={() => eqeione("6")} class=" bg-slate-200 shadow-lg text-stone-400">6</button>
  <button id="/" on:click={() => eqeione(" / ")} class=" bg-indigo-300 shadow-lg">÷</button>
  <button id='1' on:click={() => eqeione("1")} class=" bg-slate-200 shadow-lg text-stone-400">1</button>
  <button id="2" on:click={() => eqeione("2")} class=" bg-slate-200 shadow-lg text-stone-400">2</button>
  <button id="3" on:click={() => eqeione("3")} class=" bg-slate-200 shadow-lg text-stone-400 ">3</button>
  <button id="*" on:click={() => eqeione(" * ")} class=" bg-orange-100 shadow-lg">×</button>
  <button id="." on:click={() => eqeione(".")} class=" bg-slate-200 shadow-lg text-stone-400">.</button>
  <button id="0" on:click={() => eqeione("0")} class=" bg-slate-200 shadow-lg text-stone-400"  >0</button>
  <button id="=" on:click={() => solve()} class=" bg-slate-200 shadow-lg text-stone-400 col-span-2">=</button>
  
</div>

