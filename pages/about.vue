<template>
  <div id="about-page" class="page-wrapper about-page content-page">
    <site-hero
      title="¿Qué es esto?"
      subtitle="Una lista de recursos comentados"
      image="/uploads/candid-at-home.jpg"
    ></site-hero>
    <main-section theme="one-column">
      <template v-slot:default>
        <div class="content">
          <h3>El origen</h3>
          <p>
            La pandemia del COVID-19 situa a la humanidad en un punto crítico. A partir del confinamiento en los hogares para evitar la expansión del virus surge la necesidad de seguir trabajando en remoto. Muchas personas aterrizan en este formato forzadas por la situación. Este lsitado trata de ser un bálsamo para el primer aterrizaje.
          </p>

          <h3>Participa tu también</h3>
          <p>
            El apoyo a las iniciativas surgidas en la sociedad para fomentar la responsabilidad particular de cada individuo solo tienen sentido si cada uno aportamos nuestro granito de arena. 
          </p>
          <p>
            Este listado puede mejorarse y ampliarse con tus aportaciones. Para ello puedes añadir una <em>issue</em> o un </em>Pull Request</em> en el repositorio en github: <a href="https://github.com/delineas/teletrabajando-web"
                >teletrabajando-web</a
              >
          </p>
          <p>
            Si esto te suena a <em>chino</em>, escríbeme en twitter <a href="https://twitter.com/delineas">@delineas</a>
          </p>
          
          <h3>#YoMeQuedoEnCasa #FrenaLaCurva</h3>

          <h3>¿Quién está detrás?</h3>
          <p>
            Soy <a href="https://www.danielprimo.io/">Daniel Primo</a>, programador web y formador. Puedes escucharme en Web Reactiva todos los martes y leerme en La Selecta Newsletter cada domingo.
          </p>
        </div>

      </template>

      <template v-slot:sidebar>
        <h3 class="subtitle is-4">
          Latest Posts
        </h3>
        <posts-grid :per-row="1" :number="2" />
      </template>
    </main-section>
  </div>
</template>
<script>
import QuoteCard from '~/components/cards/QuoteCard'
export default {
  head() {
    return {
      title: `About | ${this.$siteConfig.siteName}`
    }
  },
  components: { QuoteCard }
}
</script>
