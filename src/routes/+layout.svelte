
    <div class="header">

        <h3>Generic Bus time App</h3>
    </div>


<slot></slot>


<style>
    * {
  margin: 0;
  padding: 10;
  box-sizing: border-box;
}

    
    :root{
        padding: 0;
        border: 0;
        --main-color: #3d8c40;

        background-color: #1f2937;
        width: 100%;

    }

    h3{
        color: white;
        font-family: Arial, Helvetica, sans-serif;
    }
    .header{
        width: 100%;
        height: 10vh;
        background-color: var(--main-color);
        padding: 0 0;
        margin-top: -7px;

        display: flex;
        flex-direction: row;
        align-items: center;
        justify-content: center;
    }

    .header h3{
        padding-left: 20px;
    }

    @media only screen and (max-width: 600px) {
        :root{
            margin: 0;

        }
}       .header{
        padding: -30px 0;
}
</style>