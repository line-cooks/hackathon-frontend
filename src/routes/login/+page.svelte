<script>
        import PocketBase from 'pocketbase';
        import {currentUser, pb} from '../../lib/pocketbase'
        let email
        let password
        let message

        

        if (currentUser == true){
            window.location.href = "/"

        }

        async function login(){
        try{
            const logIn = await pb.collection('users').authWithPassword(email,password)
            message = ''
            window.location.href = "/"
        }
        catch {
            message = "Email or password are invalid."
            
            
        }
    }


    async function signup(){
    let passwordConfirm = password
        
       const data = {
           email,
           password,
           passwordConfirm
           


       }

       try{
        const createdUser = await pb.collection('users').create(data)
       await login()

       }  
       catch {
            message = "Check your email or password. Passwords must be larger than 8 characters."
            
            
        }

       

     
   }  
    function logout(){
        pb.authStore.clear()
    }


</script>



<div class="main-site">

    {#if $currentUser}
    {/if}

    <h1>Log in or register</h1>
    <form>
        <input
        placeholder="email"
        type="text"
        class="text-input"
        bind:value={email}
        >
        <input
        placeholder="password"
        type="password"
        class="text-input"

        bind:value={password}
        >
    
        <div class="buttons">
            <button on:click={signup}>
                sign up
            </button>
        
            <button on:click={login}>
                log in
            </button>

        </div>

    </form>

    <h4>{message}</h4>

</div>
<style>

    h1{
        color: white;
        font-family: Arial, Helvetica, sans-serif;
    }

    .main-site {
        display: flex;
        flex-direction: column;
        justify-content: center;
        align-items: center;
        
        height: 70vh;
        width: 100%;
        }

    form{
        width: 50%;
        gap: 10px;
        height: 50%;
        display: flex;
        flex-direction: column;
        justify-content: center;
        padding: 10px;
    }
    .buttons{
        display: flex;
        justify-content: space-between;
        width: 100%;
        height: 15%;
    }

    button{
        width: 49%;
        background-color: var(--main-color);
        border: none;
        border-radius: 7px;

        color: white;
        font-size: larger;

    }

    input{
        height: 10%;
    }
    input:focus{
        outline: none;
    }
    .text-input{
        height: 10%;
    }
     h4{
        color: red;
        font-family: Arial, Helvetica, sans-serif;
     }
    @media only screen and (max-width: 600px) {
    form{
        width: 80%;
        justify-content:right;
    }
}
</style>