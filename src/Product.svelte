<script>
    // const products = fetch('https://localhost:5001/api/product/', {mode: 'no-cors'});
    // console.log(products);

    // const products = (async () => {
    //     const response = await fetch('https://localhost:5001/api/product/', {mode: 'no-cors'})
    //         .then(response => response.json())
    //     console.log(response)
    //     return response;
    // })()

    const products = fetch(
        "https://localhost:5001/api/product/",
        {
            // mode: "no-cors",
            method: "GET"
        }
    )
        .then(response => response.text())
        .then(data =>{
            console.log("response-----", data);
            return data
        })

</script>

    <table class="table table-responsive table-striped">
        <thead>
        <th>Name</th>
        <th>Type</th>
        <th>Price</th>
        <th>Quantity</th>
        </thead>
        <tbody>
        {#await products}
            <p>....waiting</p>
            {:then data}
        {#each data as product}
            <tr>
                <td>{data}</td>
                <td>{data}</td>
                <td>{data}</td>
            </tr>
            {/each}
            {:catch error}
            <p>An error occurred </p>
            {/await }
        </tbody>
    </table>