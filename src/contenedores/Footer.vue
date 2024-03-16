<template>
    <div class="envoltura container-fluid bg-secondary">
        <div class="icon">
            <i class="fa-solid fa-bolt"></i>ClimApp
        </div>
        <div class="description">
            <p>Lorem ipsum dolor sit amet consectetur, adipisicing elit. Corrupti perferendis, iste soluta repellendus
                temporibus in? Corrupti perferendis, iste soluta repellendus
                temporibus in</p>
        </div>
    </div>
</template>

<style scoped>

.envoltura{
    display: flex;
    justify-content: space-around;
    gap: 1rem;
    color: white;
    min-height: 8rem;
    padding: 3rem 2rem;

}

.wrapper .description{
    width: 50%;
    display: grid;    
    place-items: center;
    border-left: 1px solid white;
    padding: 0 5px;
}


.wrapper .icon {
    font-size: 2rem;
    display: flex;
    flex-direction: column;
    justify-content: center; 
}

.wrapper .icon i{
    font-size: 4rem;
    display: flex;
    justify-content: center;
    color: rgb(255, 159, 62);
}


</style>