<script>
    import Menu from './menu.svelte'
    var kcssz = 5, ivkcs
    const epml = [
        {
            szn: 'Krisztina',
            pmn: 'A backendes amit legutóbb csináltam',
            oe: 0,
            megj: []
        },
        {
            szn: 'Peti',
            pmn: 'Ez is valami cool fullstack',
            oe: 0,
            megj: []
        },
        {
            szn: 'Ádám',
            pmn: 'Csináltam egy paintet',
            oe: 0,
            megj: []
        },
        {
            szn: 'Ádám (a tanársegéd)',
            pmn: 'Radnótis cucc',
            oe: 0,
            megj: []
        },
    ]
</script>
<Menu active="Kezdőoldal"></Menu>
<h1>Kezdőoldal: Csillagozós példa</h1>
<div class="cont">
    {#each epml as ep, k}
        <!-- svelte-ignore a11y-no-static-element-interactions -->
        <div class="el" bind:this={ep.obj}
        on:drop={() => {
            if (ivkcs == null) {
                ep.oe++
                kcssz--
            } else {
                ep.oe++
                epml[ivkcs].oe--
            }
        }} 
        on:dragover={e => (e.preventDefault(), true)}>
            <b>{ep.szn}</b><br>{ep.pmn}<br>
            <div class="cskk">
                {#each Array(ep.oe).fill("*").map((v, i) => i) as i}
                <div class="csk" id="x{i}" draggable="true" on:dragstart={() => {
                    ivkcs = k
                }}>🌟</div>
                {/each}
            </div>
            
        </div>
    {/each}
</div>
<div class="cst">
    {#each Array(kcssz).fill(0) as _, i}
        <!-- svelte-ignore a11y-no-static-element-interactions -->
        <div class="cs" id="x{i}" draggable="true" on:dragstart={() => ivkcs = null}>🌟</div>
    {/each}
</div>
<style>
h1 {
    text-align: center;
}
div.cont {
    display: inline-block;
    width: 80%;
    margin: auto;
    display: grid;
    grid-template-columns: 1fr 1fr;
}
div.el {
    display: inline-block;
    text-align: center;
    height: 60px;
    padding: 20px;
    background-color: aquamarine;
    margin: 20px;
    border: silid 2px black;
    border-radius: 6px;
    box-shadow: 1px 1px 3px inset black;
}
div.cst, div.cskk {
    display: flex;
    justify-content: center;
}
div.cst {
    background-color: black;    
}
div.cs {
    display: inline-block;
    margin: 0px;
    padding: 0px;
    font-size: 80px;
    background:transparent;
    transform: translateY(-3px);
    cursor: grab;
    border-radius: 20px;
}
div.csk {
    display: inline-block;
    width: 20px;
    height: 20px;
    box-shadow: 1px 1px 4px black;
    margin: 4px;
    padding: 4px;
    font-size: 16px;
    background-color: rgb(41, 13, 68);
    cursor: grab;
    border-radius: 20px;
}
</style>