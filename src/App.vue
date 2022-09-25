<template>
  <nav-bar />
  <div class="flexbox">
    <div>
      <receipe-book
        v-for="receipe in receipes"
        :key="receipe.id"
        :name="receipe.name"
        :img="receipe.img"
        :desc="receipe.desc"
        :id="receipe.id"
        @receipeStatus="receipeStatus"
      />
    </div>
    <div>
      <receipe-details
        v-for="receipe in receipes"
        :key="receipe.id"
        :name="receipe.name"
        :img="receipe.img"
        :desc="receipe.desc"
        :id="receipe.id"
        :thatReceipe="receipe.thatReceipe"
      />
    </div>
  </div>
</template>

<script>
import NavBar from "./components/NavBar.vue";
import ReceipeBook from "./components/ReceipeBook.vue";
import ReceipeDetails from "./components/ReceipeDetails.vue";
export default {
  name: "App",
  components: { ReceipeBook, NavBar, ReceipeDetails },
  data() {
    return {
      receipes: [
        {
          id: 1,
          name: "chicken biriyani",
          img: "https://media.istockphoto.com/photos/chicken-biryani-with-yogurt-dip-popular-indian-pakistani-non-food-picture-id1254720533?b=1&k=20&m=1254720533&s=170667a&w=0&h=Ulr-m1vVGmMGdFFU0lNvX9nnKuzYhQSFI5ZIdIGYkKk=",
          desc: " Lighter on spices, Kolkata Biryani is made by using yoghurt based marinade for the meat, which is cooked separately from the light yellow rice. Method: Marinate chicken pieces with curd, red chilli powder, turmeric and salt for 45 minutes to 1 hour. Partially cook the rice with black cardamom and bay leaves.",
          receipeStatus: false,
        },
        {
          id: 2,
          name: "chicken masala",
          img: "https://media.istockphoto.com/photos/murgh-makhani-butter-chicken-tikka-masala-picture-id1262857001?b=1&k=20&m=1262857001&s=170667a&w=0&h=LDytMWvxGKBs63GhCuAxxYnG1MDibHLmNH8mij4gkPA=",
          desc: "To make Masala Chicken, first thoroughly wash the chicken under running water. Now put it in some warm salted water and allow it to rest for 10 minutes and throw the water away and wash again. This helps to remove the smell of the chicken.Add oil and ghee in pan and heat over medium flame. When the oil is hot enough, add bay leaves and both the cardamom and cinnamon. Saute for a minute and then add finely chopped onion into it. Cook till onions turn pink. Then add the ginger-garlic paste. Fry for a minute and then add chicken pieces in it. Cook chicken for 2-3 minutes until it turns white.Quickly, add red chilli powder, coriander powder, turmeric, cumin powder, and salt to taste. Stir to mix all the ingredients well with the chicken. Cook for a minute and then add finely chopped tomatoes and green chillies (slit and halved). Now reduce the flame and cook covered for 6-7 minutes and then uncovered till the chicken is browned.Add one cup water and cover the pan with a lid and cook for 2-4 minutes until the chicken is tender and soft. Remove the lid and garnish with garam masala powder, coriander leaves, kasoori methi powder and cook on high flame till the oil separates. Your Masala Chicken or Chicken Masala is ready. Enjoy with butter naan, rice or roti.",
        },
        {
          id: 3,
          name: "chicken lollipop",
          img: "https://images.slurrp.com/prod/articles/9z37p2kepve.webp",
          desc: "To the chicken start adding soy sauce, chilly sauce, red chilly powder, turmeric powder, pepper powder, garam masala, maida,ginger and garlic paste, corn flour, egg, fresh cream and salt as per taste..Mix all the ingredients till well combined cover and allow the chicken to marinate in the counter top for 2 hours or place the chicken in a container and refrigerate over night...for best results...Just before frying add few drops of red food color and mix well..Heat oil in a wok on medium flame once the oil is hot drops the chicken lollipop",
        },
      ],
    };
  },
  methods: {
    receipeStatus(receipeID) {
      console.log("receipeID from child to parent", receipeID);
      let identifiedReceipe = this.receipes.find(
        (receipe) => receipe.id === receipeID
      );
      console.log("identifiedReceipe", identifiedReceipe);
      identifiedReceipe.thatReceipe = !identifiedReceipe.thatReceipe;
    },
  },
};
</script>

<style>
.flexbox {
  display: flex;
}
</style>
