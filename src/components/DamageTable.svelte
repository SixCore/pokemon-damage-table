<script>
    let positive = "../img/positive.png";
    let negative = "../img/negative.png";
    let cross = "../img/cross.png";
    let empty = "../img/empty.png";

    let typesObj = [
        {"type": "Normal", "color": "#aaa878"},
        {"type": "Feuer", "color": "#f07f2f"},
        {"type": "Wasser", "color": "#6890f0"},
        {"type": "Pflanze", "color": "#79c950"},
        {"type": "Elektro", "color": "#f8d030"},
        {"type": "Eis", "color": "#98d8d8"},
        {"type": "Kampf", "color": "#c13129"},
        {"type": "Gift", "color": "#a040a1"},
        {"type": "Boden", "color": "#e0c069"},
        {"type": "Flug", "color": "#a98ff0"},
        {"type": "Psycho", "color": "#f95989"},
        {"type": "Käfer", "color": "#a9b821"},
        {"type": "Gestein", "color": "#b7a038"},
        {"type": "Geist", "color": "#715699"},
        {"type": "Drache", "color": "#7038f9"},
        {"type": "Unlicht", "color": "#6f5848"},
        {"type": "Stahl", "color": "#b8b8d0"},
        {"type": "Fee", "color": "#f7c9e3"},
    ]

    let stats = [0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, -1, "x", 0, 0, -1, 0,
                 0, -1, -1, 1, 0, 1, 0, 0, 0, 0, 0, 1, -1, 0, -1, 0, 1, 0,
                 0, 1, -1, -1, 0, 0, 0, 0, 1, 0, 0, 0, 1, 0, -1, 0, 0, 0,
                 0, -1, 1, -1, 0, 0, 0, -1, 1, -1, 0, -1, 1, 0, -1, 0, -1, 0,
                 0, 0, 1, -1, -1, 0, 0, 0, "x", -1, 0, 0, 0, 0, -1, 0, 0, 0,
                 0, -1, -1, 1, 0, -1, 0, 0, 1, 1, 0, 0, 0, 0, 1, 0, -1, 0,
                 1, 0, 0, 0, 0, 1, 0, -1, 0, -1, -1, -1, 1, "x", 0, 1, 1, -1,
                 0, 0, 0, 1, 0, 0, 0, -1, -1, 0, 0, 0, -1, -1, 0, 0, "x", 1,
                 0, 1, 0, -1, 1, 0, 0, 1, 0, "x", 0, -1, 1, 0, 0, 0, 1, 0,
                 0, 0, 0, 1, -1, 0, 1, 0, 0, 0, 0, 1, -1, 0, 0, 0, -1, 0,
                 0, 0, 0, 0, 0, 0, 1, 1, 0, 0, -1, 0, 0, 0, 0, "x", -1, 0,
                 0, -1, 0, 1, 0, 0, -1, -1, 0, -1, 1, 0, 0, -1, 0, 1, -1, -1,
                 0, 1, 0, 0, 0, 1, -1, 0, -1, 1, 0, 1, 0, 0, 0, 0, -1, 0,
                 "x", 0, 0, 0, 0, 0, 0, 0, 0, 0, 1, 0, 0, 1, 0, -1, -1, 0,
                 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 1, 0, -1, "x",
                 0, 0, 0, 0, 0, 0, -1, 0, 0, 0, 1, 0, 0, 1, 0, -1, -1, -1,
                 0, -1, -1, 0, 0, 1, 0, 0, 0, 0, 0, 0, 1, 0, 0, 0, -1, 1,
                 0, -1, 0, 0, 0, 0, 1, -1, 0, 0, 0, 0, 0, 0, 1, 1, -1, 0];
</script>

<div class="box">
    <div class="def-text">
        Verteidigendes Pokémon
    </div>
    <div class="def-types">
        {#each typesObj as typeObj}
            <div class="type" style="background: {typeObj.color}">{typeObj.type}</div>
        {/each}
    </div>
    <div class="att-text">
        Angreifendes Pokémon
    </div>
    <div class="att-types">
        {#each typesObj as typeObj}
            <div class="type" style="background: {typeObj.color}">{typeObj.type}</div>
        {/each}
    </div>
    <div class="chart">
        {#each stats as stat}
            <div class="stat">
                {#if stat === 1}
                    <img src={positive} alt="effective"/>
                {:else if stat === -1}
                    <img src={negative} alt="not effective" />
                {:else if stat === "x"}
                    <img src={cross} alt="no damage" />
                {:else}
                    <img src={empty} alt="no effect" />
                {/if}
            </div>
        {/each}
    </div>
</div>

<style>
    .box {
        display: grid;
        gap: 2px;
        grid-template-columns: repeat(20, 1fr);
        grid-template-rows: repeat(18, 1fr);
        max-height: 100vh;
        max-width: 100vw;
    }
    .def-text {
        grid-column: 3 / 21;
        grid-row: 1 / 2;
        text-align: center;
        padding: 10px;
        background-color: slategrey;
        color: whitesmoke;
        font-size: 21px;
    }
    .def-types {
        grid-column: 3 / 21;
        grid-row: 2 / 3;
        display: flex;
        justify-content: space-around;
    }
    .def-types .type {
        writing-mode: vertical-lr;
        transform: rotate(-180deg);
        flex-shrink: 1;
        flex-grow: 1;
        flex-basis: 5.5%;
    }
    .att-text {
        grid-column: 1 / 2;
        grid-row: 3 / 19;
        writing-mode: vertical-lr;
        transform: rotate(-180deg);
        background-color: slategrey;
        color: whitesmoke;
        font-size: 21px;
        text-align: center;
        padding: 10px;
    }
    .att-types {
        grid-column: 2 / 3;
        grid-row: 3 / 19;
        display: flex;
        flex-direction: column;
        justify-content: space-around;
    }
    .att-types .type {
        height: 5.5%;
    }
    .type {
        color: whitesmoke;
    }
    .chart {
        grid-column: 3 / 21;
        grid-row: 3 / 19;
        display: flex;
        flex-wrap: wrap;
        justify-content: center;
        align-items: center; 
    }
    .chart .stat {
        flex: 1 0 5.5%;
        box-sizing: border-box;
        text-align: center;
        max-height: 5.5%;
        font-size: 21px;
    }
    .stat > img {
        width: 100%;
        height: auto;
        max-width: 25px;
        max-height: auto;
    }
    @media (max-width: 480px) {
        .def-text, .att-text {
            font-size: 16px;
        }
        .def-types, .att-types {
            font-size: 0.7em;
        }
    }
</style>

