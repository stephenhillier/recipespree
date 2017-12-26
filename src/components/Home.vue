<template>
  <div>
    <section class="hero header-image">
      <div class="hero-body">
        <div class="container">
          <h1 class="title">
            Get inspired
          </h1>
          <h2 class="subtitle">
            Find a recipe, get the shopping list, make something amazing
          </h2>
        </div>
      </div>
    </section>

    <div class="box cta">
      <p class="has-text-centered">
        <span class="tag is-primary">New</span> Star your favorite recipes! Clicking the star also lets you find it easily later.
      </p>
    </div>

      <div class="container">
        <h1 class="title has-text-primary" style="padding-bottom:1rem">
          Featured recipes
        </h1>
      </div>
      <div class="container has-text-centered">
        <div class="tile is-ancestor">
          <div class="tile">
            <div class="tile is-parent"
              v-if="recipes"
              v-for="recipe in recipes"
              :key="recipe.id">
              <article class="tile is-child notification">

                  <div class="card">

                  <div class="card-image">
                    <figure class="image">
                      <div style='position:relative; padding-bottom:57%'><iframe :src='recipe.url' frameborder='0' scrolling='no' width='100%' height='100%' style='position:absolute;top:0;left:0;' allowfullscreen></iframe></div>
                    </figure>
                  </div>
                  <div class="card-content">
                    <div class="tabs is-toggle is-fullwidth">
                      <ul>
                        <li class="is-active"><a>Video</a></li>
                        <li><a>Shopping List</a></li>
                        <li><a>Directions</a></li>
                      </ul>
                    </div>
                    <div class="media">
                      <div class="media-left">

                          <span class="icon has-text-warning" style="margin-top: 0.5rem">
                            <i v-if="recipe.is_starred === true" class="fa fa-2x fa-star" @click="recipe.is_starred = !recipe.is_starred"></i>
                            <i v-else class="fa fa-2x fa-star-o" @click="recipe.is_starred = !recipe.is_starred"></i>
                          </span>
                      </div>
                      <div class="media-content">
                        <p class="title is-4">{{ recipe.name }}</p>
                        <p class="subtitle is-6">By: <a>{{ recipe.from }}</a> on {{ recipe.added }}</p>
                      </div>
                    </div>

                    <div class="content has-text-left">
                      <p>{{ recipe.description }}
                      <span 
                      v-if="recipe.tags"
                      v-for="tag in recipe.tags"
                      :key="tag">
                      <a href="#">#{{ tag }}</a>&nbsp;</span>
                      </p>
                    </div>
                  </div>
                </div>
              </article>
            </div>
          </div>
        </div>
      </div>
  </div>
</template>

<script>
export default {
  name: 'Home',
  data () {
    return {
      recipes: [
        {
          id: 1,
          name: 'One Pan Baby Back Ribs',
          from: 'gfycat',
          description: 'Get your bbq fix without braving the elements. Bonus: one dish to wash (if you eat off the pan)',
          tags: ['bbqsauce', 'ribs'],
          url: 'https://gfycat.com/ifr/UltimateEllipticalAmericanrobin?autoplay=0',
          added: 'November 8, 2017',
          stars: 15,
          is_starred: true
        },
        {
          id: 2,
          name: 'Pizza Burger',
          from: 'gfycat',
          description: 'Can\'t decide between burgers or pizza for that romantic dinner you had planned? Now you don\'t have to choose!',
          tags: ['grease', 'burgers'],
          url: 'https://gfycat.com/ifr/ImaginaryHospitableAquaticleech?autoplay=0',
          added: 'November 8, 2017',
          stars: 2,
          is_starred: false
        }
      ]
    }
  }
}
</script>
<style lang="css" scoped>
.header-image {
    background-image: url("../assets/img/cupcakes2.jpg");
    background-position: center center;
    background-repeat: no-repeat;
    background-attachment: fixed;
    background-size: cover;
    background-color: #999;
}
</style>