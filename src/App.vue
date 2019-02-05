<template>
    <div class="bg-image">
        <div class="container">
            <div class="row justify-content-center">
                <h1>Meet our team</h1>
            </div>
            <div class="row justify-content-center">

                <div class="col-sm-6 col-md-4 col-xl-2 team-member" v-for="person in people">
                    <div class="team-member-picture mx-auto">
                        <div class="color-image"></div>
                        <img class="image justify-content-md-center" v-bind:src="person.image">
                        <div class="email">
                            <i class="fas fa-envelope icon-envelope"></i>
                        </div>
                    </div>
                    <p class="person-name">{{person.name}} {{person.surname}}</p>
                    <p class="person-position">{{person.position}}</p>
                    <p class="person-city">{{person.city}}</p>
                </div>
            </div>
        </div>

    </div>
</template>

<script>
    export default {

        data() {
            return {
                people: [
                    {
                        name: 'Anna',
                        surname: 'Kowalska',
                        position: 'Founder',
                        city: 'Warsaw',
                        image: require('./assets/photo-1.jpg')

                    },
                    {
                        name: 'Emilia',
                        surname: 'Zarzycka',
                        position: 'Human Resources',
                        city: 'London',
                        image: require('./assets/photo-2.jpg')
                    },
                    {
                        name: 'Anna',
                        surname: 'Tomala',
                        position: 'IT Helpdesk',
                        city: 'Warsaw',
                        image: require('./assets/photo-3.jpg')
                    },
                    {
                        name: 'Zenon',
                        surname: 'Fabiszewski',
                        position: 'Business Development',
                        city: 'Warsaw',
                        image: require('./assets/photo-4.jpg')
                    },
                    {
                        name: 'Marek',
                        surname: 'Maczek',
                        position: 'Head of Communication',
                        city: 'London',
                        image: require('./assets/photo-5.jpg')
                    },
                    {
                        name: 'Anna',
                        surname: 'Mroczek',
                        position: 'Head of Communication',
                        city: 'Warsaw',
                        image: require('./assets/photo-6.jpg')
                    },
                    {
                        name: 'Natalia',
                        surname: 'Mucha',
                        position: 'Human Resources Specialist',
                        city: 'London',
                        image: require('./assets/photo-7.jpg')
                    },
                    {
                        name: 'Anna',
                        surname: 'Nosowska-Tomczak',
                        position: 'Customer support',
                        city: 'Warsaw',
                        image: require('./assets/photo-8.jpg')
                    },
                    {
                        name: 'Tomasz',
                        surname: 'Miodowski',
                        position: 'Business Development',
                        city: 'Warsaw',
                        image: require('./assets/photo-9.jpg')
                    },
                    {
                        name: 'Kamil',
                        surname: 'Kisielewski',
                        position: 'Head of Communication',
                        city: 'London',
                        image: require('./assets/photo-10.jpg')
                    },


                ]
            }
        },
    }
</script>
<style>
    .bg-image {
        background-repeat: repeat;
        width: 100vw;
        height: 100vh;
    }

    .bg-image::after {
        content: "";
        background-image: url("./assets/bg.png");
        opacity: 0.3;
        top: 0;
        left: 0;
        bottom: 0;
        right: 0;
        position: absolute;
        z-index: -1;
    }

    h1 {
        color: #452e76;
        font-size: 45px;
        margin-top: 45px;
        margin-bottom: 60px;
        font-family: 'Open Sans', sans-serif;
    }

    .image {
        width: 155px;
        height: auto;
        border-radius: 50%;
        text-align: center;
    }

    .color-image {
        position: absolute;
        top: 0;
        bottom: 0;
        left: 0;
        right: 0;
        height: 100%;
        width: 100%;
        border-radius: 50%;
        transition: .5s ease;
        background-color: #48c3dc;
        opacity: 0.7;
    }

    .team-member-picture:hover .color-image {
        opacity: 0;
    }

    .person-name {
        margin-top: 20px;
        font-weight: 400;
        color: #452e76;
        text-align: center;
        font-family: 'Open Sans', sans-serif;
    }

    .person-position {
        font-size: 14px;
        color: #48c3dc;
        text-align: center;
        font-family: 'Open Sans', sans-serif;
    }

    .person-city {
        font-size: 12px;
        color: #969696;
        text-align: center;
        font-family: 'Open Sans', sans-serif;
    }

    .email {
        width: 35px;
        height: 35px;
        background-color: #452e76;
        position: absolute;
        border-radius: 50%;
        right: 3px;
        top: 3px;
        text-align: center;
        line-height: 35px;
    }

    .icon-envelope {
        color: white;
        display: inline-block;
        line-height: normal;
    }

    .team-member-picture {
        position: relative;
        width: 155px;
    }

    .team-member {
        margin-top: 30px;
    }

    @media (min-width: 1200px) {
        .team-member {
            flex: 0 0 20%;
            max-width: 20%;
            text-align: center;
        }
    }

    @media (max-width: 576px) {
        h1 {
            font-size: 30px;
        }
    }
</style>
