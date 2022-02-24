<template>
  <div class="col text-center">
        <div class="card">
            <img :src="disco.poster">
            <h5>{{disco.title}}</h5>
            <div>
                <span>{{disco.author}}</span> <br>
                <span>{{disco.year}}</span>
            </div>
        </div>
    </div>
</template>

<script>
export default {
    name: 'MyDisco',
    props: {
        disco: Object
    }
}
</script>

<style lang="scss" scoped>

    .col {
        width: 140px;
        color: white;
        padding: 10px;
        

        .card {
            background-color: #2e3a46;
            padding: 10px;
            height: 300px;
            display: flex;
            flex-direction: column;
            align-items: center;
            justify-content: space-between;

            h5 {
                text-transform: uppercase;
            }

            span {
                color: grey;
            }
        }
    }
    img {
        width: 120px;
        height: 120px;
    }
</style>

