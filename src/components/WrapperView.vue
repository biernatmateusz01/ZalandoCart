<template>
  <div class="relative w-full min-h-screen py-4">
    <div
      class="flex flex-wrap items-center justify-center w-full px-1.5 container max-w-7xl m-auto"
    >
      <ProductItem
        v-for="product in productsList"
        :key="product.id"
        :product="product"
        @addItem="addItemToShoppingCart(product)"
      />
    <div ></div>
    </div>
    <ShoppingCart :yourProducts="yourProducts" />
  </div>
</template>

<script>
import ProductItem from "./ProductItem.vue";
import ShoppingCart from "../components/ShoppingCart.vue";

export default {
  components: {
    ProductItem,
    ShoppingCart,
  },
  emits: {
    addItem: null,
  },

  data() {
    return {
      yourProducts: [],
      productsList: [
        {
          id: 1,
          photo:
            "https://img01.ztat.net/article/spp-media-p1/16599894562b46b68a67e0cc461f4940/d33aa8327ec34ebaab972bee29a7508e.jpg?imwidth=1800",
          secondPhoto:
            "https://img01.ztat.net/article/spp-media-p1/92f6ea96b7bc488aa0cc1e267206a76a/c39cf36fe6d5496985ed35619cb2af95.jpg?imwidth=1800",
          price: "1619.00",
          productName: "NUDISTCURVE - Sandały na obcasie",
          brand: "Stuart Weitzman",
          sale: "15",
        },
        {
          id: 2,
          photo:
            "https://img01.ztat.net/article/spp-media-p1/8e0b6e2521814a488ddf341a55e2a1ff/5e42d47598c3493fa0edae7c31ddb1b8.jpg?imwidth=762&filter=packshot",
          secondPhoto:
            "https://img01.ztat.net/article/spp-media-p1/0c0c9db0615c4690a036407953901e1d/78b18a61e3894eed88d1073166ac1fb1.jpg?imwidth=1800",

          price: "458.00",
          productName: "ALEXIE TOP ZIP SHOULDER BAG SET - Torba na ramię",
          brand: "Guess",
          discountCode: "W5T8MLNV",
        },
        {
          id: 3,
          photo:
            "https://img01.ztat.net/article/spp-media-p1/17d24b25fa1f4595854f40f4361bba03/bf260b7bda374e3ba3cddd10486a0a5f.jpg?imwidth=1800",
          secondPhoto:
            "https://img01.ztat.net/article/spp-media-p1/a53340f8b5ba4f039eeb3d191162d68d/fb404de791a34ffca53760f94e7cd88e.jpg?imwidth=1800",
          price: "125.00",
          productName: "LOW CUT SHOE CHICAGO - Obuwie treningowe",
          brand: "Champion",
          discountCode: "W5T8MLNV",
        },
        {
          id: 4,
          photo:
            "https://img01.ztat.net/article/spp-media-p1/65c66d3979e8357a803feead3a8d7282/6b6abfa87c9748d6927e675cdd09a2af.jpg?imwidth=1800",
          secondPhoto:
            "https://img01.ztat.net/article/spp-media-p1/4b8580e51a2f372089e2731b0241c560/545a6891650945e98a8203700d9d3b38.jpg?imwidth=1800&filter=packshot",
          price: "195.00",
          productName: "BERTOLETI JACKET - Kurtka sportowa",
          brand: "Ellesse",
          discountCode: "W5T8MLNV",
        },
        {
          id: 5,
          photo:
            "https://img01.ztat.net/article/spp-media-p1/6e81c667c70f3155b0851ea7f7ce6d1b/c82119333c6242c18428763270c25a17.jpg?imwidth=1800&filter=packshot",
          secondPhoto:
            "https://img01.ztat.net/article/spp-media-p1/e04d3d172ffc39cdaa6cd79d8f17bd21/518c03f29d144e419d95e656f130ff2e.jpg?imwidth=1800",
          price: "299.95",
          productName: "JJEMOULDER COAT - Klasyczny płaszcz",
          brand: "Jack & Jones",
          sale: "5",
          discountCode: "W5T8MLNV",
        },
        {
          id: 6,
          photo:
            "https://img01.ztat.net/article/spp-media-p1/25d15da5788447f8a3c39f2bbcb1d17e/c4f62f29e62c43668f36c7d657acfe73.jpg?imwidth=1800&filter=packshot",
          secondPhoto:
            "https://img01.ztat.net/article/spp-media-p1/e4bab0e5b5384d979b6a3ec18577f313/0b0a9a5b311e407aa3ae944d4ac47610.jpg?imwidth=1800",
          price: "369.00",
          productName: "PREDATOR EDGE.3 FG - Korki Lanki",
          brand: "adidas Performance",
        },
        {
          id: 7,
          photo:
            "https://img01.ztat.net/article/spp-media-p1/5cd731fc73b230fe8e0d9915dc4ccd89/1cae7052ff804aa28805d46bd4d5143a.jpg?imwidth=1800&filter=packshot",
          secondPhoto:
            "https://img01.ztat.net/article/spp-media-p1/5bc8132a759b3e49aa073b2d6c699428/013d624eed214349b5ade4e6cf76f610.jpg?imwidth=1800",
          price: "174.00",
          productName: "CHAMP - Kurtka sportowa",
          brand: "JAKO",
        },
        {
          id: 8,
          photo:
            "https://img01.ztat.net/article/spp-media-p1/1da3e69843d842a98200ffb25c4984ba/aaa3517c67e54126aea0a78c016119e1.jpg?imwidth=1800&filter=packshot",
          // secondPhoto:
          //   "https://img01.ztat.net/article/spp-media-p1/4be58654adc74d8cbb88993e760a9c47/1bdc9e97504d46b1a88aaa0488bf9852.jpg?imwidth=1800&filter=packshot",
          price: "265.30",
          productName: "Kask",
          brand: "Quiksilver",
          sale: "25",
        },
        {
          id: 9,
          photo:
            "https://img01.ztat.net/article/spp-media-p1/0494476c44e93c928c885d28ea68d9a5/2901af50dea04083acc47fd660743ff2.jpg?imwidth=1800&filter=packshot",
          secondPhoto:
            "https://img01.ztat.net/article/spp-media-p1/38741bc6fdf7324ba7e7af6341840cbf/f20bc83d13f64111b31882f8d3aea1d6.jpg?imwidth=1800",
          price: "79.19",
          productName: "BANDANA UNISEX 2 PACK - Chusta",
          brand: "Urban Classics",
          sale: "10",
        },
        {
          id: 10,
          photo:
            "https://img01.ztat.net/article/spp-media-p1/19e9fbe6edb6395890ab609b97c3c6ed/0eaeaa44273d44fe97a1e385130685bd.jpg?imwidth=1800&filter=packshot",
          secondPhoto:
            "https://img01.ztat.net/article/spp-media-p1/987ae18ddc3e3bf4aede42937130e1ba/c8ed3fda3865419282b9d2e88a24c3b2.jpg?imwidth=1800",
          price: "231.00",
          productName: "ORIGINAL STRETCH - Koszula ",
          brand: "Tommy Jeans",
          sale: "5",
          discountCode: "W5T8MLNV",
        },
        {
          id: 11,
          photo:
            "https://img01.ztat.net/article/spp-media-p1/cb076ecefc724ad69bb25f39dc5a2a3f/658f71f123404e9f8ddc857c93399b8a.jpg?imwidth=1800&filter=packshot",
          secondPhoto:
            "https://img01.ztat.net/article/spp-media-p1/0c6becdfb7cb4f92b02a47758af6d413/5a082f69f79c4381b77a510df2a372a8.jpg?imwidth=1800",
          price: "549.00",
          productName: "AIR FORCE 1 '07 LV8 - Sneakersy niskie",
          brand: "Nike Sportswear ",
          sale: "30",
        },
        {
          id: 12,
          photo:
            "https://img01.ztat.net/article/spp-media-p1/fb58b7ec09033c8eb73e13084912426c/f6a40de3c2a84fc3a7f30f140367b514.jpg?imwidth=1800&filter=packshot",
          secondPhoto:
            "https://img01.ztat.net/article/spp-media-p1/f6008410fffe31dabfd6ebcf0053ebb2/ee37e5b78d044ec9af436b62980a01ef.jpg?imwidth=1800",
          price: "129.00",
          productName: "CAROUSEL 3 PACK - Stringi",
          brand: "Calvin Klein Underwear ",
        },
        {
          id: 13,
          photo:
            "https://img01.ztat.net/article/spp-media-p1/4b7f15d1d6ed4ecf86e154198c5da646/d88ca52add524aa0a52ab9b07bca8b39.jpg?imwidth=1800&filter=packshot",
          secondPhoto:
            "https://img01.ztat.net/article/spp-media-p1/4d313684ca6c43eeae25d14beca3bf13/ec8e66ad62f545a285bdd685ebb40e53.jpg?imwidth=1800",
          price: "139.00",
          productName: "MADISON LOGO UNISEX - Czapka z daszkiem",
          brand: "Carhartt WIP",
          discountCode: "W5T8MLNV",
        },
        {
          id: 14,
          photo:
            "https://img01.ztat.net/article/spp-media-p1/7e8863fc725f4a9faccf1c70da63333b/ee51a91a75504bf9967caf5e2a445b08.jpg?imwidth=1800&filter=packshot",
          secondPhoto:
            "https://img01.ztat.net/article/spp-media-p1/5b96f50ec1424055a56c9477ebc298e5/e7e1fd501bda43c5a1ffa8887aa10c46.jpg?imwidth=1800",
          price: "119.00",
          productName: "Nerka",
          brand: "Jordan",
          discountCode: "W5T8MLNV",
        },
        {
          id: 15,
          photo:
            "https://img01.ztat.net/article/spp-media-p1/a7d0d30b277a368dbbe42fbefecc1687/fa999d6513084619b957d15d0c9e06cc.jpg?imwidth=1800&filter=packshot",
          secondPhoto:
            "https://img01.ztat.net/article/spp-media-p1/b584adcae9763da480932ef86d0ccf1d/f0e7fa146bc74242bc6b0eccf9aa6add.jpg?imwidth=1800",
          price: "144.00",
          productName: "3 PACK - T-shirt basic",
          brand: "Calvin Klein Golf ",
        },
        {
          id: 16,
          photo:
            "https://img01.ztat.net/article/spp-media-p1/b830eb8026fc42c4984305e9a55b9c67/29885b2c78b14979bf7b2dbb8a263241.jpg?imwidth=1800&filter=packshot",
          secondPhoto:
            "https://img01.ztat.net/article/spp-media-p1/b468c5dd6b684eb6ae0d712ce26250b1/62591de187c34a9fbd008a890cae0077.jpg?imwidth=1800",
          price: "109.00",
          productName: "AQUAPOWER CLEANSER - Oczyszczanie twarzy",
          brand: "Biotherm",
          discountCode: "W5T8MLNV",
        },
        {
          id: 17,
          photo:
            "https://img01.ztat.net/article/spp-media-p1/b5ddc9c2c9d63200a8876f3f52115cd9/d5f5457bb77545d2ac6d1826eaad6ddb.jpg?imwidth=1800",
          secondPhoto:
            "https://img01.ztat.net/article/spp-media-p1/24a873b1bd0d3d08a7d3b257099cedce/a476923f0bb34bbca3e4dba0da4758ff.jpg?imwidth=1800",
          price: "77.00",
          productName: "MID BATWING FLEXFIT UNISEX - Czapka z daszkiem",
          brand: "Levi's®",
          discountCode: "W5T8MLNV",
        },
        {
          id: 18,
          photo:
            "https://img01.ztat.net/article/spp-media-p1/2905314bbafa4cd88d9716b66327f43f/2c60b708709a4605bf52c5bdf079ddcc.jpg?imwidth=1800",
          secondPhoto:
            "https://img01.ztat.net/article/spp-media-p1/d5f44f1fa94349cb90b58e84f978192a/08da9acca1df4c658688fbfef7a81030.jpg?imwidth=1800&filter=packshot",
          price: "379.00",
          productName: "ARSENAL LONDON H - Artykuły klubowe",
          brand: "adidas Performance",
        },
        {
          id: 19,
          photo:
            "https://img01.ztat.net/article/spp-media-p1/b9a2804a2e6b3b7a8869b0f7e1088ca8/24e6cd22124d4a948045d03b5779f50d.jpg?imwidth=1800&filter=packshot",
          secondPhoto:
            "https://img01.ztat.net/article/spp-media-p1/494f86feeb1431c38d728d698bb5c5cf/df978f637ebd4a00ae602d0dcf09e69b.jpg?imwidth=1800",
          price: "649.00",
          productName: "AIR MAX 90 UNISEX - Obuwie do golfa",
          brand: "Nike Golf",
        },
        {
          id: 20,
          photo:
            "https://img01.ztat.net/article/spp-media-p1/8395f1f3042348c8af698992e2ac7e33/1136b672913f48bdaf8f7408030dc056.jpg?imwidth=1800&filter=packshot",
          secondPhoto:
            "https://img01.ztat.net/article/spp-media-p1/028347238ec04a238782a84daf1c831c/1cf50f77cb5c437688b544a1be20ca0d.jpg?imwidth=1800",
          price: "229.00",
          productName: "FUTURE 4.3 MG - Korki Lanki",
          brand: "Puma",
        },
        {
          id: 21,
          photo:
            "https://img01.ztat.net/article/spp-media-p1/767887f29c8e4b09b8da54137be1a1b4/8de8ebafad3847e1b4469ad7975bb547.jpg?imwidth=1800",
          secondPhoto:
            "https://img01.ztat.net/article/spp-media-p1/3c3e37944d9b4780bf503f08bdd9afed/d08ec228f1ae44fc8e1722c2f704f352.jpg?imwidth=1800",
          price: "182.75",
          productName: "Koszula",
          brand: "Trendyol",
          discountCode: "W5T8MLNV",
        },
        {
          id: 22,
          photo:
            "https://img01.ztat.net/article/spp-media-p1/d49f8b87b269420ab04e0656f6e733a9/4664bf9ed5ca4464b0ba8760c783c6b4.jpg?imwidth=1800",
          secondPhoto:
            "https://img01.ztat.net/article/spp-media-p1/712044f606c34cf7b0659c72c1e412f8/ffff87aeb98c44fbac18fbe4415ccf6f.jpg?imwidth=1800&filter=packshot",
          price: "42.00",
          productName: "CROSS NECKLACE - Naszyjnik",
          brand: "River Island",
        },
        {
          id: 23,
          photo:
            "https://img01.ztat.net/article/spp-media-p1/d9fcec14a4724a9cbab761315cc6a239/cc3852b3e0c346deb89e72945885f2f1.jpg?imwidth=1800&filter=packshot",
          secondPhoto:
            "https://img01.ztat.net/article/spp-media-p1/1ad3542959454d4f8d8cc8fce4c4f300/0c94d0e070a1464dac3d6e1cc645b900.jpg?imwidth=1800",
          price: "379.99",
          productName: "LIVERPOOL FC - Artykuły klubowe",
          brand: "Nike Performance",
        },
        {
          id: 24,
          photo:
            "https://img01.ztat.net/article/spp-media-p1/8104d94278933cfea35ce1301d79bb16/34e9c7f3abfb4d2aa8bea5f8d9c40c81.jpg?imwidth=1800&filter=packshot",
          secondPhoto:
            "https://img01.ztat.net/article/spp-media-p1/83490da003ea3d4c9556c365cdead483/d4a2e2410c3742c4b67ea8a705226cda.jpg?imwidth=1800",
          price: "197.00",
          productName: "BISTRO - Drewniaki i Chodaki",
          brand: "Crocs",
          sale: "5",
        },
        {
          id: 25,
          photo:
            "https://img01.ztat.net/article/spp-media-p1/033da1d756fe4949a62ab82f46995e1c/1880f95567af419fa28ee9ef311f2915.jpg?imwidth=1800",
          secondPhoto:
            "https://img01.ztat.net/article/spp-media-p1/ea7d3d67f96b417da1f9bf754ae4dc4f/23de03cfb68e4dce89a656d34ff0c564.jpg?imwidth=1800&filter=packshot",
          price: "197.00",
          productName:
            "BLUE & BEYOND - BLUE LIGHT & PHOTOCHROMIC UNISEX - Okulary z filtrem światła niebieskiego",
          brand: "Mont Blanc",
          discountCode: "W5T8MLNV",
        },
        {
          id: 26,
          photo:
            "https://img01.ztat.net/article/spp-media-p1/69812486fe4d4639b3eb1aa6521603c9/303b6fa275e5403aacfeb89825c398d6.jpg?imwidth=1800&filter=packshot",
          secondPhoto:
            "https://img01.ztat.net/article/spp-media-p1/5290d862d0c9412abd9278da01ffb078/cf69d36b326441f495ca18c106ed7aae.jpg?imwidth=1800",
          price: "59.00",
          productName: "MINI BALLON AL RIHLA - Piłka do piłki nożnej",
          brand: "adidas Performance",
          sale: "15",
        },
        {
          id: 27,
          photo:
            "https://img01.ztat.net/article/spp-media-p1/e1dac7f54fb246beaf26b8e8566d716f/b1f311a53a304787abd1333c64d4be63.jpg?imwidth=1800&filter=packshot",
          secondPhoto:
            "https://img01.ztat.net/article/spp-media-p1/40cb1b3d1c744f459d12610984ddffb9/cd38de75492641879bf754f5868aa212.jpg?imwidth=1800",
          price: "599.00",
          productName: "XT-WINGS 2 UNISEX - Sneakersy niskie",
          brand: "Salomon",
          sale: "10",
        },
        {
          id: 28,
          photo:
            "https://img01.ztat.net/article/spp-media-p1/8d4567daa8c94d05bee9100fdce229f3/a32727e3576f4a3595208929b0a90653.jpg?imwidth=762",
          secondPhoto:
            "https://img01.ztat.net/article/spp-media-p1/4c627780e790480d875bd4761a5d3848/25d4259294694b9f9e051d637a1c46e3.jpg?imwidth=1800&filter=packshot",
          price: "1599.00",
          productName: "Kurtka puchowa",
          brand: "Polo Sport Ralph Lauren",
          sale: "20",
        },
        {
          id: 29,
          photo:
            "https://img01.ztat.net/article/spp-media-p1/77808fc2a3bc4414a308484c199d6daa/6586c538d5ec42c391ef6130dc41cf89.jpg?imwidth=1800",
          secondPhoto:
            "https://img01.ztat.net/article/spp-media-p1/e4a19020afc44953b1e176acd024c0ad/a5bc517907954977801aa1ae5db8a324.jpg?imwidth=1800",
          price: "249.00",
          productName: "Szorty",
          brand: "Nike Sportswear",
        },
        {
          id: 30,
          photo:
            "https://img01.ztat.net/article/spp-media-p1/89e098f600484f449e0d36533d6b2f07/4546ad615a5141e3a9e4a963ab591264.jpg?imwidth=762",
          secondPhoto:
            "https://img01.ztat.net/article/spp-media-p1/3f826d358d1749838cbee032aa657c13/f0ccb8064d89416bb93007b524df1e96.jpg?imwidth=762&filter=packshot",
          price: "379.00",
          productName: "REAL MADRID - Artykuły klubowe",
          brand: "adidas Performance",
        },
        {
          id: 31,
          photo:
            "https://img01.ztat.net/article/spp-media-p1/c25f7e30b8c543e1ad3abc77569e28bd/13bae004e8404adbb01abee501ca171d.jpg?imwidth=1800",
          secondPhoto:
            "https://img01.ztat.net/article/spp-media-p1/b0a319bfadc8456c9fb80473284a995d/f75f65a3949842eeaf5df1992f61ce34.jpg?imwidth=1800",
          price: "130.00 ",
          productName: "TECH - T-shirt basic",
          brand: "Under Armour",
        },
        {
          id: 32,
          photo:
            "https://img01.ztat.net/article/spp-media-p1/14df49f5ecbc4bbbb26711862efdcb7b/66bbf77f4cd443059b2f4c23c165f930.jpg?imwidth=1800",
          secondPhoto:
            "https://img01.ztat.net/article/spp-media-p1/b0a9a5a684ae487881431da9c05b1d1d/35d63c4a6b8642fc8f01fba231c74ef7.jpg?imwidth=1800&filter=packshot",
          price: "619.00",
          productName: "CASCADE SHIELD JACKET - Kurtka Softshell",
          brand: "Helly Hansen",
        },
        {
          id: 33,
          photo:
            "https://img01.ztat.net/article/spp-media-p1/84742ac842b14e31ac6f4e58b0267bcc/6fb705a4c20e4a95a63441212b827fa9.jpg?imwidth=1800&filter=packshot",
          secondPhoto:
            "https://img01.ztat.net/article/spp-media-p1/2c9db016c39749c6bb3d31379511f03d/ab2f6a3c1b8d4c968a8a97551fc40f5e.jpg?imwidth=1800",
          price: "819.00",
          productName: "LUNAR NEW YEAR POLO BEAR HOODIE - Bluza",
          brand: "Polo Ralph Lauren",
        },
        {
          id: 34,
          photo:
            "https://img01.ztat.net/article/spp-media-p1/48637992543b4b3280df09608347c52d/18a0b7e745364459baca67abb7741f87.jpg?imwidth=1800&filter=packshot",
          secondPhoto:
            "https://img01.ztat.net/article/spp-media-p1/25fc4bddd7eb40af9960d4d2d57f3c83/5684f79253d1438a98482cadd2f7d18d.jpg?imwidth=1800",
          price: "314.00",
          productName: "AJAX AWAY AMSTERDAM AEROREADY - Artykuły klubowe",
          brand: "adidas Performance",
        },
        {
          id: 35,
          photo:
            "https://img01.ztat.net/article/spp-media-p1/2714537b083e456a81bf396a9f177fe0/92f5d8a8034942b8a6bb59d012f25322.jpg?imwidth=1800",
          secondPhoto:
            "https://img01.ztat.net/article/spp-media-p1/2eed41b1483540b99f1bec0d578f8071/e7ca3d739101475aa7e1aab8c5121267.jpg?imwidth=1800",
          price: "179.00",
          productName: "OPEN TEE - T-shirt z nadrukiem",
          brand: "Nike Sportswear",
        },
        {
          id: 36,
          photo:
            "https://img01.ztat.net/article/spp-media-p1/d0fb9b4b7147462cb208394025edabf3/c48de4be4d0c45238a6949621f076a5a.jpg?imwidth=1800",
          secondPhoto:
            "https://img01.ztat.net/article/spp-media-p1/e09952c05b634c0bb49ac34dc0c5d918/2b1159f1c4e345128df05dd9ade1d921.jpg?imwidth=1800&filter=packshot",
          price: "189.00",
          productName: "HAT UNSIEX - Czapka z daszkiem",
          brand: "Guess",
        },
        {
          id: 37,
          photo:
            "https://img01.ztat.net/article/spp-media-p1/ae161ffc0e244bbb93eecee44f9b1b85/2c9f1d118ecd4211858c35340ac53c04.jpg?imwidth=1800&filter=packshot",
          secondPhoto:
            "https://img01.ztat.net/article/spp-media-p1/1c2f2b10e5c24224852ea92f5e4a56e8/261ddc48459a44df9c98a548ab08c0d5.jpg?imwidth=1800",
          price: "71.00",
          productName: "Paris Serie Expert Blondifier Shampoo Cool - Szampon",
          brand: "L'OREAL PROFESSIONNEL",
          discountCode: "W5T8MLNV",
        },
        {
          id: 38,
          photo:
            "https://img01.ztat.net/article/spp-media-p1/92f85b2cfe084afa81ba7027a640e95e/08b60d51627643cf9beaa7d9a68b4f7b.jpg?imwidth=1800&filter=packshot",
          secondPhoto:
            "https://img01.ztat.net/article/spp-media-p1/62cb4cf7a8384c1a9f1f1d81f5add227/ed1521094c0f455ea10f06e70c513997.jpg?imwidth=1800",
          price: "144.00",
          productName: "HAT UNSIEX - Czapka z daszkiem",
          brand: "Guess",
        },
        {
          id: 39,
          photo:
            "https://img01.ztat.net/article/spp-media-p1/124980c71ac84676af8668eeeb6acc7d/fe97ad1a5fe44d3a8dfa30942c4a25b0.jpg?imwidth=762",
          secondPhoto:
            "https://img01.ztat.net/article/spp-media-p1/77cce736a8b94aabbd6f8ea1d2d8bd62/bd296f9d0a5b4a1aa82c93664646a54b.jpg?imwidth=1800&filter=packshot",
          price: "84.00",
          productName:
            "MINNIE MOUSE + MICKEY & FRIENDS 2 PACK - T-shirt z nadrukiem",
          brand: "Staccato",
        },
        {
          id: 40,
          photo:
            "https://img01.ztat.net/article/spp-media-p1/53bae677f43a422bba45ea2fc754ad7a/9d41c5b85b3d40758ef32be285d52905.jpg?imwidth=1800",
          secondPhoto:
            "https://img01.ztat.net/article/spp-media-p1/6b4af3768bc84371a628435b3e31aace/8e162aea417b490085c282820cf97f3a.jpg?imwidth=1800&filter=packshot",
          price: "59.90",
          productName: "Legginsy",
          brand: "Stradivarius",
        },
        {
          id: 41,
          photo:
            "https://img01.ztat.net/article/spp-media-p1/a516442086d74106beb8ba09c5c406a4/a27f9aa1e4c242bda56323a2b9fcb974.jpg?imwidth=1800&filter=packshot",
          secondPhoto:
            "https://img01.ztat.net/article/spp-media-p1/a9c2fb055b8347779241207f8eacbf74/09f060987a8f46569eda021d84fbd71b.jpg?imwidth=762",
          price: "59.90",
          productName: "BY NEW SKOOL BACKPACK BOYS - Tornister",
          brand: "Vans",
        },
        {
          id: 42,
          photo:
            "https://img01.ztat.net/article/spp-media-p1/5f0f23391bc14603ad7b969f5e998fd4/f161ca0d7afa40fa9665fd7e18415840.jpg?imwidth=1800&filter=packshot",
          secondPhoto:
            "https://img01.ztat.net/article/spp-media-p1/18fa2d7a406343eb8c36d685de39a144/2eb195cc4b76441fa46360a550025a87.jpg?imwidth=1800",
          price: "239.00",
          productName: "REAL MADRID H MINI SET UNISEX - Artykuły klubowe",
          brand: "adidas Performance",
        },
        {
          id: 43,
          photo:
            "https://img01.ztat.net/article/spp-media-p1/637fe59eff084e149857b03e48636e7f/a11e36bf798d4ee19b54a731a83cd3d2.jpg?imwidth=1800",
          secondPhoto:
            "https://img01.ztat.net/article/spp-media-p1/91861e4afea94c94a127f59c8bfce376/1dc6a3840b4347da9e89f150c6faff4c.jpg?imwidth=1800&filter=packshot",
          price: "59.00",
          productName: "LOGO GIRLS - Spodnie treningowe",
          brand: "GAP",
        },
        {
          id: 44,
          photo:
            "https://img01.ztat.net/article/spp-media-p1/e6e8dc61e0a731cba20ab1a0cb83d1d7/a4714dbb91f840e58105ff0fe2f9cf1b.jpg?imwidth=1800&filter=packshot",
          secondPhoto:
            "https://img01.ztat.net/article/spp-media-p1/b983a36083a93f3ebc47d3f6f00432f2/ba941f1041a84772974165f0869ce29d.jpg?imwidth=1800",
          price: "287.00",
          productName: "ARIZONA - Klapki",
          brand: "Birkenstock",
        },
        {
          id: 45,
          photo:
            "https://img01.ztat.net/article/spp-media-p1/f8b466fb26b639599d557ffff04e4b46/df5edb452fb24353add1d5a684deba7f.jpg?imwidth=1800",
          secondPhoto:
            "https://img01.ztat.net/article/spp-media-p1/5a635c84206433d7a899d43e2408e685/2a54e9aa40ff42e1960150088c8fc99f.jpg?imwidth=1800&filter=packshot",
          price: "101.00",
          productName: "LOGO UNISEX - T-shirt basic",
          brand: "Lacoste Sport",
        },
        {
          id: 46,
          photo:
            "https://img01.ztat.net/article/spp-media-p1/96bb1bfdc93737bdb9dcedfcbb31a99d/a4dd5dc808534e83a1ca5d73193c77b4.jpg?imwidth=1800&filter=packshot",
          secondPhoto:
            "https://img01.ztat.net/article/spp-media-p1/132a10cb060b3f338c3660806aa6e1d9/87a9e976f8ad415087af9af63d2fe9d7.jpg?imwidth=1800",
          price: "339.00",
          productName: "RAINFOREST WINTER - Kurtka przejściowa",
          brand: "Napapijri",
        },
        {
          id: 47,
          photo:
            "https://img01.ztat.net/article/spp-media-p1/0d6a40165c0a455fab847bc4e59eab23/d65ad44a1bd84a9f86aeddfdb319b0e3.jpg?imwidth=1800&filter=packshot",
          secondPhoto:
            "https://img01.ztat.net/article/spp-media-p1/f89f946ad556465fb693779b52efd1ec/0033b0b8dd9b45a4a969ce9cad09c288.jpg?imwidth=762",
          price: "95.00",
          productName: "ISLAND - T-shirt z nadrukiem - türkis",
          brand: "Blue Seven",
        },
        {
          id: 48,
          photo:
            "https://img01.ztat.net/article/spp-media-p1/156cd263962d355e85b183225e873f64/2f7ecc8c836a49af8218371b21fb6115.jpg?imwidth=1800&filter=packshot",
          secondPhoto:
            "https://img01.ztat.net/article/spp-media-p1/26175be8af7231b28371b7c4a9a034d4/65d39861d3a94902895a3ba8b1d6e3f5.jpg?imwidth=1800",
          price: "101.00",
          productName: "CROCBAND KIDS UNISEX - Sandały kąpielowe",
          brand: "Crocs",
          discountCode: "W5T8MLNV",
        },
        {
          id: 49,
          photo:
            "https://img01.ztat.net/article/spp-media-p1/c1e4f4373aaa3ed2b28beaa49ce2a7b4/8ac54fa919044ab5a92cb80c3f2e5c78.jpg?imwidth=1800",
          secondPhoto:
            "https://img01.ztat.net/article/spp-media-p1/38e48c6c80603e278f6e73b58eac7bc9/83c2e9bff76747129ec2aa9c1ea3be64.jpg?imwidth=1800",
          price: "84.00 ",
          productName: "Bluzka z długim rękawem",
          brand: "adidas Originals",
          sale: "10",
        },
        {
          id: 50,
          photo:
            "https://img01.ztat.net/article/spp-media-p1/8bafac9843bb443f8627719d4549d62f/93c4109194ba402994e6d4a8959737c1.jpg?imwidth=1800&filter=packshot",
          secondPhoto:
            "https://img01.ztat.net/article/spp-media-p1/715d8d0dfdf840979f82c7cba6b8b732/e113010ef094416c9c667a86e35f8cd3.jpg?imwidth=1800",
          price: "599.99",
          productName: "PARIS ST GERMAIN MATCH - Artykuły klubowe",
          brand: "Nike Performance",
          sale: "5",
          discountCode: "W5T8MLNV",
        },
        {
          id: 51,
          photo:
            "https://img01.ztat.net/article/spp-media-p1/3d38fb8a9cd949a79d9cf318fd947948/3244f47228e04d638804c0fe37068f30.jpg?imwidth=1800&filter=packshot",
          secondPhoto:
            "https://img01.ztat.net/article/spp-media-p1/0fe18576ef3f4b8ebfd3de2f44ede343/9b2f6af0819946af9aea4a79697c0d46.jpg?imwidth=1800",
          price: "169.00",
          productName: "SHORTALL GIRL - Ogrodniczki",
          brand: "GAP",
          sale: "8",
        },
        {
          id: 52,
          photo:
            "https://img01.ztat.net/article/spp-media-p1/2030be2a9185470a8877a1b50eafb144/fe7f1213521746ff870d6b551e03b80d.jpg?imwidth=1800",
          secondPhoto:
            "https://img01.ztat.net/article/spp-media-p1/7549aec9cb2a42faa54370d2a7829c7f/c46e88c10a454c0ab688e7b8d8479c19.jpg?imwidth=1800",
          price: "699.00",
          productName: "OMBR� FRENCH TERRY SWEATSHIRT - Bluza",
          brand: "Polo Ralph Lauren",
        },
        {
          id: 53,
          photo:
            "https://img01.ztat.net/article/spp-media-p1/11e32e6fb5c0480eb1320ffb53aa700e/42c596f2cd7f459b801efc3f885beac2.jpg?imwidth=1800",
          secondPhoto:
            "https://img01.ztat.net/article/spp-media-p1/59b2fd2db28e4838b3ee4d7779b99529/31c07dc410c14ae6b14487889d04c40e.jpg?imwidth=1800",
          price: "54.00",
          productName: "Sneakersy niskie ",
          brand: "Even&Odd",
        },
        {
          id: 54,
          photo:
            "https://img01.ztat.net/article/spp-media-p1/c01a4c62c1c3411d883696b3d2627587/344e319d7d4c4297aef570a02d09949c.jpg?imwidth=1800&filter=packshot",
          secondPhoto:
            "https://img01.ztat.net/article/spp-media-p1/26af81e6d09c45f189ccfdd8a4579b18/5b744c10701f418b824822cd0076b5f3.jpg?imwidth=1800",
          price: "119.00",
          productName: "LEOPARD UP - Góra od bikini",
          brand: "Hunkemöller",
          discountCode: "W5T8MLNV",
        },
        {
          id: 55,
          photo:
            "https://img01.ztat.net/article/spp-media-p1/afc6247ce8714bfbb45bbbe8e585860a/b5d3f33c56e54585948eea10baaed4a4.jpg?imwidth=1800",
          secondPhoto:
            "https://img01.ztat.net/article/spp-media-p1/d8938540580744f98af8f7d3307bc8a6/d04120103f0f45caadd39c4c9c8e863d.jpg?imwidth=1800",
          price: "162.70 ",
          productName: "Spodnie materiałowe",
          brand: "Trendyol",
        },
        {
          id: 56,
          photo:
            "https://img01.ztat.net/article/spp-media-p1/ef961045f4eb48d4907380cb7339857d/65de76e50f4c43afa1555ed26df52201.jpg?imwidth=762&filter=packshot",
          secondPhoto:
            "https://img01.ztat.net/article/spp-media-p1/dbed8bc4cadd417cbc41329d5763c26b/88624df6f2644b8c92b7d31378757dc5.jpg?imwidth=1800",
          price: "357.00",
          productName: "NIMA - Kurtka jeansowa",
          brand: "Von Dutch",
        },
        {
          id: 57,
          photo:
            "https://img01.ztat.net/article/spp-media-p1/a0e9a48473214a05a103e253c33dfbec/606db65ded364a428e75348f87ceb617.jpg?imwidth=1800",
          secondPhoto:
            "https://img01.ztat.net/article/spp-media-p1/cba179f3183d47cdae41e7a7a093b9ec/8512c0fb2524452fa23bd33243c11498.jpg?imwidth=1800",
          price: "357.00",
          productName: "STAN SMITH UNISEX - Sneakersy niskie",
          brand: "adidas Originals",
        },
        {
          id: 58,
          photo:
            "https://img01.ztat.net/article/spp-media-p1/7dad5b7ef67e3bd69634061f6b00a42e/0e57d31d623e4883a2e79483b4b2716b.jpg?imwidth=1800&filter=packshot",
          secondPhoto:
            "https://img01.ztat.net/article/spp-media-p1/677aba44503639ddb3aa9261dd03cc36/4e8906c1360f4785973bb35c22fa2c40.jpg?imwidth=1800",
          price: "54.00",
          productName: "BEARD BRUSH (SMALL) - Szczotka do włosów",
          brand: "Beyer's Oil",
        },
        {
          id: 59,
          photo:
            "https://img01.ztat.net/article/spp-media-p1/7f96d58a432949779053fa912b649f7b/7ed4df7b24664a82bad5ec91e5d12787.jpg?imwidth=1800&filter=packshot",
          secondPhoto:
            "https://img01.ztat.net/article/spp-media-p1/bb38eef5571449ef8aa6ff854ff8f8b8/c7995dc63372483a9e962fbd42b96fa7.jpg?imwidth=1800",
          price: "53.00",
          productName:
            "EVERYDAY PLUS CUSH CREW 3 PACK UNISEX - Skarpety sportowe",
          brand: "Nike Performance",
          sale: "10",
        },
        {
          id: 60,
          photo:
            "https://img01.ztat.net/article/spp-media-p1/32f10a9fe96549d99779d3d3c21dd4e9/94efed2cfbde4080940ab2cfba80e74c.jpg?imwidth=1800&filter=packshot",
          secondPhoto:
            "https://img01.ztat.net/article/spp-media-p1/ccc371e46d9943e298ce21fb4390613b/7df7122ac4044a83a4555e40b9b6b21f.jpg?imwidth=1800",
          price: "489.00 ",
          productName: "AIR JORDAN 1 MID - Sneakersy wysokie",
          brand: "Jordan",
          sale: "15",
        },
        {
          id: 61,
          photo:
            "https://img01.ztat.net/article/spp-media-p1/93a70f052b843780847e4e04a4631062/ab71d0cd061b462db4204661eff992e1.jpg?imwidth=1800&filter=packshot",
          secondPhoto:
            "https://img01.ztat.net/article/spp-media-p1/b5d3235c8e8a3594b48298fcac8fb313/86809aba78244d2d931661cf8342ce22.jpg?imwidth=1800",
          price: "54.00",
          productName:
            "THE RITUAL OF SAMURAI FACE CHARCOAL SCRUB - Peeling do twarzy",
          brand: "Rituals",
          sale: "5",
          discountCode: "W5T8MLNV",
        },
        {
          id: 62,
          photo:
            "https://img01.ztat.net/article/spp-media-p1/4df70485058b4a409b05a461df17caad/7bb97488420b462d889f4312dfd0eeb8.jpg?imwidth=1800",
          secondPhoto:
            "https://img01.ztat.net/article/spp-media-p1/1c8fff937f444e4aba9b96e4aef66aef/54011d95753f4394b1c8ca9071c1b82a.jpg?imwidth=1800",
          price: "159.00",
          productName: "DYNAMIC TECH TEE - T-shirt z nadrukiem",
          brand: "SIKSILK",
        },
        {
          id: 63,
          photo:
            "https://img01.ztat.net/article/spp-media-p1/5ec6eb47a994420196c54df793cb8405/6e848982b5b5471c83fedcb4713f194d.jpg?imwidth=1800&filter=packshot",
          secondPhoto:
            "https://img01.ztat.net/article/spp-media-p1/7eccd1edae5d40409ca221b1968a071d/bd0a6bd31e82440bbe4b4dbf353d3590.jpg?imwidth=1800",
          price: "939.00",
          productName: "ENDORPHIN PRO 2 - Obuwie do biegania startowe",
          brand: "Saucony",
        },
        {
          id: 64,
          photo:
            "https://img01.ztat.net/article/spp-media-p1/5211f05f2fd74a6fac17be9966dd380e/fc8af798b1b5426e9351d35f1ed8075e.jpg?imwidth=1800&filter=packshot",
          secondPhoto:
            "https://img01.ztat.net/article/spp-media-p1/ac0b213dcdc54fdb896dd19db43f041a/70597aa9c0ef46fe881bb0e23a5c3969.jpg?imwidth=1800",
          price: "99.00",
          productName: "BLOSSOM BUNNY MEDIUM UNISEX - Pluszowa maskotka",
          brand: "Jellycat",
        },
        {
          id: 65,
          photo:
            "https://img01.ztat.net/article/spp-media-p1/2a16cd9113d2489294a30f145e8e9a2b/990fcf72198c4965b1037da917e53154.jpg?imwidth=1800&filter=packshot",
          secondPhoto:
            "https://img01.ztat.net/article/spp-media-p1/9f7aa0714c844ea0bfc18d0ff7082bb7/c03a31a2a3454f548fc3b78bfd447d4b.jpg?imwidth=762",
          price: "99.00",
          productName: "7 PACK DAYS OF THE WEEK - Figi",
          brand: "Next",
        },
        {
          id: 66,
          photo:
            "https://img01.ztat.net/article/spp-media-p1/24bfb9ca60513cbc9b6ce1497364d670/31ed4f4a2ab04f23b1e931b4f08d2409.jpg?imwidth=1800",
          secondPhoto:
            "https://img01.ztat.net/article/spp-media-p1/5f74d11edac934498cc15292585caf59/b256f48698b94fbbb0f659dcbe79a68d.jpg?imwidth=1800",
          price: "926.00",
          productName: "SCHOOL ADVENTURE TIPI SET - Zestaw szkolny",
          brand: "Lässig",
          discountCode: "W5T8MLNV",
        },
        {
          id: 67,
          photo:
            "https://img01.ztat.net/article/spp-media-p1/48e08e3a619b45a0bfc8f2eee9c5ed1d/f1c2b4c8fa754a7a891a8214ad9e56bb.jpg?imwidth=1800&filter=packshot",
          secondPhoto:
            "https://img01.ztat.net/article/spp-media-p1/e06290b333f840d99b8f9fce563a7352/8c89dc4785e64acf93a13e33372663fe.jpg?imwidth=762",
          price: "110.00",
          productName: "BOY - Piżama",
          brand: "GAP",
          discountCode: "W5T8MLNV",
        },
        {
          id: 68,
          photo:
            "https://img01.ztat.net/article/spp-media-p1/ad72afa6c58e44428fc06be61453ba69/5d5c9b54ed084410b9e956022a496653.jpg?imwidth=1800&filter=packshot",
          secondPhoto:
            "https://img01.ztat.net/article/spp-media-p1/5f632cbd895c4a29be36fd56cdb2bf60/3ec7044c1284456ba47f4f16bbd5840d.jpg?imwidth=1800",
          price: "169.00",
          productName: "5 PACK - T-shirt basic",
          brand: "Abercrombie & Fitch",
          sale: "10",
          discountCode: "W5T8MLNV",
        },
      ],
    };
  },
  methods: {
    addItemToShoppingCart(product) {
      this.yourProducts.push(product);
      alert("Dodano produkt do koszyka !");
    },
  },
};
</script>
