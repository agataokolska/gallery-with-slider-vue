<template>
    <div class="bg-image">
        <div class="container">
            <div class="row justify-content-center">
                <h1>Meet our team</h1>
            </div>
            <div class="row justify-content-center">

                <div class="col-sm-6 col-md-4 col-xl-2 team-member" v-for="person in people">
                    <div class="team-member-picture mx-auto"
                         @click="showSlider(person.name, person.surname, person.position)">
                        <div class="color-image"></div>
                        <img class="image justify-content-md-center"
                             v-bind:src="person.image"
                        >
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

        <div class="slider-background d-flex justify-content-center align-items-center" v-if="isSlider">
            <div class="slider-navigation">
                <img class="angle-left"
                     :src="angleLeft"
                     @click="prevSlide(people.name, people.surname, people.position)"
                >
                <img class="angle-right"
                     :src="angleRight"
                     @click="nextSlide(people.name, people.surname, people.position)"
                >
                <img class="close-button"
                     :src="closeButton"
                     @click="isSlider = false"
                >
            </div>
            <div class="container">
                <div class="row">
                    <div class="slider-person-box align-middle align-items-center offset-1 col-10">
                        <p class="slider-person-position">{{currentSlideData.position || people.position}}</p>
                        <p class="slider-person-name">{{currentSlideData.name || people.name}}
                            {{currentSlideData.surname ||people.surname}}</p>
                    </div>
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


                ],
                isSlider: false,
                angleLeft: require('./assets/angle-left.png'),
                angleRight: require('./assets/angle-right.png'),
                closeButton: require('./assets/close.png'),

                currentSlideData: [{
                    name: "",
                    surname: "",
                    position: ""
                }]
            }
        },
        methods: {
            showSlider(name, surname, position) {
                if (this.isSlider === false) {
                    this.isSlider = true
                    this.people.name = name
                    this.people.surname = surname
                    this.people.position = position
                } else {
                    return this.isSlider = false
                }
            },
            nextSlide(name, surname, position) {
                this.isSlider = true
                this.people.name = name
                this.people.surname = surname
                this.people.position = position

                let index = this.people.findIndex(obj => obj.name === this.people.name && obj.surname === this.people.surname && obj.position === this.people.position)
                if (index >= this.people.length - 1) {
                    index = 0
                } else {
                    index += 1
                }

                this.people.name = this.people[index].name
                this.people.surname = this.people[index].surname
                this.people.position = this.people[index].position

                this.currentSlideData.push({
                    name: this.people[index].name,
                    surname: this.people[index].surname,
                    position: this.people[index].position
                })

            },
            prevSlide(name, surname, position) {
                this.isSlider = true
                this.people.name = name
                this.people.surname = surname
                this.people.position = position

                let index = this.people.findIndex(obj => obj.name === this.people.name && obj.surname === this.people.surname && obj.position === this.people.position)
                if (index === 0) {
                    index = (this.people.length - 1)
                } else {
                    index -= 1
                }

                this.people.name = this.people[index].name
                this.people.surname = this.people[index].surname
                this.people.position = this.people[index].position

                this.currentSlideData.push({
                    name: this.people[index].name,
                    surname: this.people[index].surname,
                    position: this.people[index].position
                })

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
        opacity: 0.2;
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
        font-weight: 600;
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

    .slider-background {
        position: fixed;
        top: 0;
        bottom: 0;
        left: 0;
        right: 0;
        background-image: url("./assets/slider-background.jpg");
        background-size: cover;
        background-repeat: no-repeat;
        background-position: center;
    }

    .slider-person-position {
        font-size: 35px;
        color: white;
        text-align: center;
        font-family: 'Open Sans', sans-serif;
        text-shadow: 1px 1px 0 #444343;
    }

    .slider-person-name {
        font-size: 70px;
        color: white;
        text-align: center;
        font-family: 'Open Sans', sans-serif;
        text-shadow: 2px 1px 0 #444343;
    }

    .slider-person-box {
        border: 5px dashed rgba(230, 230, 230, 0.2);
        padding: 30px;
    }

    .angle-left {
        position: absolute;
        left: 0px;
        top: 50%;
        margin-top: -64px;
    }

    .angle-right {
        position: absolute;
        right: 0px;
        top: 50%;
        margin-top: -64px;
    }

    .close-button {
        position: absolute;
        right: 10px;
        top: 10px;
        width: 80px
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

    @media (max-width: 740px) {
        .angle-left {
            width: 100px
        }

        .angle-right {
            width: 100px
        }

        .close-button {
            width: 70px
        }

        .slider-person-name {
            font-size: 60px;
        }

        .slider-person-position {
            font-size: 30px
        }
    }

    @media (max-width: 600px) {
        .angle-left {
            width: 90px
        }

        .angle-right {
            width: 90px
        }

        .close-button {
            width: 60px
        }

        .slider-person-name {
            font-size: 50px;
        }

        .slider-person-position {
            font-size: 25px
        }
    }

</style>
