<script>
export default {
    name: "Character",
    props: ["msg"]
}
</script>
<!-- {{ msg }} -->

<template>
    <div class="card">

        <img :src="msg.image" alt="">


        <div class="name">
            {{ msg.name }}
        </div>
        <div class="origin">
            Rick & Morty
        </div>
        <div class="status">
            {{ msg.status }}
        </div>
    </div>

</template>

<style lang="scss" scoped>
$w-Card : 130px;

.card {
    display: flex;
    flex-direction: column;
    align-items: center;
    background-color: #323c48;
    width: $w-Card;
    height: calc($w-Card * 1.5);
    padding: 10px;
    margin: 10px;
}



img {
    width: 100%;
    height: auto;
}

.name {
    color: white;
    font-size: 12px;
    font-weight: 600;
    margin-top: 5px;
}

.origin {
    color: #606264;
    font-size: 11px;
    font-weight: 500;
    margin-top: 10px;

}

.status {
    color: #606264;
    font-size: 11px;
    font-weight: 600;
    margin-top: 2px;
}
</style>
