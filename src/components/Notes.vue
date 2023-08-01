<script setup>

</script>

<template>
 <main>
    <div class="container">
        <header>
            <h1>
                Notes
            </h1>
            <button>+</button>
        </header>
        <div class="cards-container">
            <div class="card">
                <p class="main-text">

                </p>
                <p class="date">

                </p>
            </div>
        </div>
    </div>
 </main>
</template>

<style scoped>
main{
    height: 100vh;
    width: 100vw;
}
.container{
    max-width: 100px;
    padding: 10px;
    margin: 0 auto;
}
header{
    display: flex; 
    justify-content: space-around;
    align-items: center;
}
button {
    margin-left: 500px;
    border: none;
    padding: 10px 20px;
    /* height: 50px;
    width: 50px; */
    cursor: pointer;
    background-color: rgb(21, 20, 20);
    border-radius: 50%; /* Set to 50% to create a perfect circle */
    color: white;
    font-size: 20px;
}


h1{
    font-weight: bold;
    margin-bottom: 25px;
    font-size: 75px;
}
.card{
    width: 225px;
    height: 225px;
    background-color: aquamarine;
    padding: 10px;
    border-radius: 15px;
    display: flex;
    flex-direction: column;
    justify-content: space-around;
    margin-right: 20px;
    margin-bottom: 20px
}
</style>
