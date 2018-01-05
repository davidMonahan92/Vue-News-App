<template>
  <div class="newslist">

    <div class="container">
    	<ul class="media-list">
    		<li class="media" v-for="article in articles">

    			<div class="media-left">
					<a v-bind:href="article.url" target="_blank">
						<img class="media-object" v-bind:src="article.urlToImage">
					</a>
    			</div><!--End of media-left div-->

    			<div class="media-body">
    				<h4 class="media-heading">
    					<a v-bind:href="article.url" target="_blank">{{article.title}}</a>
    				</h4>
    				<h5><i>by {{article.author}}</i></h5>
    				<p>{{article.description}}</p>

    			</div><!--End of media-body article-->

    		</li><!--End media list-->

    	</ul><!--End of unorder list-->

    </div><!--End of container div-->

  </div><!-- End of newslist div-->
</template>

<script>
export default {
  name: 'newslist',
  props: ['source'],
  data () {
  	return {
  		articles: []
  	}
  },
  methods: {
  	updateSource: function(source){
  		this.$http.get('https://newsapi.org/v1/articles?source='+ source + '&apiKey=b028aa752fce4b68a913738c05829c6e').then(response => {
  			this.articles = response.data.articles;
  		});
  	}
  },
  created: function(){
  	this.updateSource(this.source); 
  },
  watch: {
  	source: function (val) {
  		this.updateSource(val);
  	}
  }
}
</script>

<style scoped>
	.media-object {
		width: 128px;
		padding: 10px;
	}
	.media {
		border-top: 1px solid lightgrey;
		padding-top: 20px;
	}
</style>
