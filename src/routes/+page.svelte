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
            pmn: 'Ez is valami fasza fullstack',
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
<h1>Kezdőoldal: Csillagozós példa</h1>
<div class="cont">
    {#each epml as ep, k}
        <!-- svelte-ignore a11y-no-static-element-interactions -->
        <div class="el" on:drop={() => {
            if (ivkcs == null) {
                ep.oe++
                kcssz--
            } else {
                ep.oe++
                epml[ivkcs].oe--
            }
            
        }} on:dragover={e => (e.preventDefault(), true)}>
            {ep.szn}<br>{ep.pmn}<br>
            <div class="cskk">
                {#each Array(ep.oe).fill("*").map((v, i) => i) as i}
                <div class="csk" id="x{i}" draggable="true" on:dragstart={() => {
                    ivkcs = k
                }}>*</div>
                {/each}
            </div>
            
        </div>
    {/each}
</div>
<div class="cst">
    {#each Array(kcssz).fill("*") as cs, i}
        <!-- svelte-ignore a11y-no-static-element-interactions -->
        <div class="cs" id="x{i}" draggable="true" on:dragstart={() => ivkcs = null}>{cs}</div>
    {/each}
</div>
<hr>
<Menu active="Kezdőoldal"></Menu>
<style>
div.cont {
    display: inline-block;
    width: 80%;
    margin: auto;
    display: grid;
    grid-template-columns: 1fr 1fr 1fr 1fr 1fr;
}
div.el {
    display: inline-block;
    text-align: center;
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
div.cs {
    display: inline-block;
    margin: 20px;
    padding: 20px;
    font-size: 40px;
    background-color: blueviolet;
    cursor: grab;
    border-radius: 20px;
}
div.csk {
    display: inline-block;
    margin: 4px;
    padding: 4px;
    font-size: 10px;
    background-color: blueviolet;
    cursor: grab;
    border-radius: 20px;
}
</style>