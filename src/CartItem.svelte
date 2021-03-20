<script>
    let products = 'https://localhost:5001/api/product/';
</script>

    <table class="table table-responsive table-striped">
        <thead>
        <th>Name</th>
        <th>Type</th>
        <th>Price</th>
        <th>Quantity</th>
        </thead>
        <tbody>
        {#each products as product}
            <tr>
                <td>product.Name</td>
                <td>product.Type</td>
                <td>product.Price</td>
                <td>product.Quantity</td>
            </tr>
            {/each}
        </tbody>
    </table>