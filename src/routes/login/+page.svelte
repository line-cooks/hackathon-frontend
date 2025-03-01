<script>
        import PocketBase from 'pocketbase';
        import {currentUser, pb} from '../../lib/pocketbase'
        let email
        let password
        let message

        async function login(){
        try{
            const logIn = await pb.collection('users').authWithPassword(email,password)
            message = ''
            window.location.href = "/"
        }
        catch {
            message = 'Username or Password is incorrect'
            console.log(message)
      
            
        }
    }


    async function signup(){
    let passwordConfirm = password
        
       const data = {
           email,
           password,
           passwordConfirm
           


       }

       const createdUser = await pb.collection('users').create(data)
       await login()

     
   }  
    function logout(){
        pb.authStore.clear()
    }


</script>

{#if $currentUser}
    <h1>Were so back</h1>
{/if}

<form>
    <input
    placeholder="email"
    type="text"
    bind:value={email}
    >
    <input
    placeholder="password"
    type="text"
    bind:value={password}
    >

    
    <button on:click={signup}>
        sign up
    </button>

    <button on:click={login}>
        log in
    </button>
</form>