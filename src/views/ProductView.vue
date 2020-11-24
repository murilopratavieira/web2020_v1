<template>
  <div class="home">
    <h1>{{ product.name }}</h1>
    <Product :images="product.images"/>
    
    
    <h2>Preço: R$ {{ product.quantity * product.price }}</h2>

    <h3>Tamanhos</h3>
    <v-radio-group v-model="row" row>
      <v-radio label="PP" value="PP"></v-radio>
      <v-radio label="P" value="P"></v-radio>
      <v-radio label="M" value="m"></v-radio>
      <v-radio label="G" value="G"></v-radio>
      <v-radio label="GG" value="GG"></v-radio>
    </v-radio-group>              
    <h3>Quantidade</h3>
    <v-text-field                
      v-model="product.quantity"
      type="number"
      outlined
      style="width:100px"
      :value="1"
      min="1"
      dense                                                  
    ></v-text-field> 

    <v-tabs>
      <v-tab>DESCRIÇÃO</v-tab>            
      <v-tab-item>
        <p> {{ product.description }}</p>
      </v-tab-item>
    </v-tabs>  

<!-- BOTAO ADICIONAR CARRINHO -->
    <div class="center">
      <v-btn href="/carrinho" color="primary" class="mb-8 black--text" large>
      <v-icon>mdi-cart</v-icon> Adicionar o Carrinho
    </v-btn>           
    </div>
  
<!-- Produtos relacionados -->
    <p class="text-center">Produtos Relacionados</p>
    <v-divider></v-divider>
    <div class="row text-center">
      <div class="col-md-4 text-center">
        <v-hover
          v-slot:default="{ hover }"
          open-delay="200"
          >
          <v-card
            :elevation="hover ? 16 : 2"
            >
            <v-img
              class="white--text align-end"
              height="100%"
              :src="require('../assets/moletom.png')"
              >                      
            </v-img>
            <div>Moletom Canguru</div>
            <div>
              <v-btn href="/produto" class="ma-2" outlined>
                Ver
              </v-btn>
            </div>
          </v-card>
        </v-hover>
      </div>

      <div class="col-md-4 text-center">
        <v-hover
          v-slot:default="{ hover }"
          open-delay="200"
          >
          <v-card
            :elevation="hover ? 16 : 2"
            >
            <v-img
              class="white--text align-end"
              height="100%"
              :src="require('../assets/moletom.png')"
              >                      
            </v-img>
            <h3>Moletom Canguru</h3>
            <div class="text-center">
              <v-btn href="/produto" class="ma-2" outlined>
                Ver
              </v-btn>
            </div>
          </v-card>
        </v-hover>
      </div>

      <div class="col-md-4 text-center">
        <v-hover
          v-slot:default="{ hover }"
          open-delay="200"
          >
          <v-card
            :elevation="hover ? 16 : 2"
            >
            <v-img
              class="white--text align-end"
              height="100%"
              :src="require('../assets/moletom.png')"
              >                      
            </v-img>
            <h3>Moletom Canguru</h3>                    
            <div class="text-center">
              <v-btn href="/produto" class="ma-2" outlined>
                Ver
              </v-btn>
            </div>
          </v-card>
        </v-hover>
      </div>
    </div>
  </div>
  
</template>

<script>
import Product from "@/components/Product";

export default {
  name: "Home",
  data: () => {
    return {
      product: {
        images: ["moletom.png", "moletom2.png"],
        name: "Moletom Canguru",
        description:
          "Os moletons são feitas em ótima qualidade e esse produto é apenas para compras em atacado",
        price: 110.99,
        quantity: 1,
        cores: null,
        tamanho: null,
      },
    };
  },
  components: {
    Product,
  },
};
</script>

<style lang="scss" scoped>
.home {
  width: 100vw;
  max-width: 768px;
  overflow: hidden;
  margin: 0 auto;
}

.price {
  text-align: center;
  font-weight: bold;
  font-size: 2.5rem;
}

.quantity {
  text-align: center;
  border: 3px solid #c3c3c3;
}

.price_text {
  text-align: center;
  font-weight: bold;
  font-size: 1.5rem;
}

h1 {
  text-align: center;
  padding: 16px;
  margin: 16px 0 0;
  font-family: Galada, arial;
  font-size: 3rem;
}

h2 {
  text-align: center;
  padding: 16px;
  margin: 16px 0 0;
  font-family: Galada, arial;
  font-size: 2rem;
}

p {
  padding: 16px;
  margin: 0;
  font-family: Abel, arial;
  font-size: 1.3rem;
}

.title {
  color: black;
}

.quantity-text {
  display: flex;
}

.order {
  padding: 16px;

  .quantidade {
    border: black;
  }
}

.center {
  display: flex;
  justify-content: center;
}

</style>
