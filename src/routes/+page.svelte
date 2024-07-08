<!-- --background-color: #eedacc;
--search-background-color: #ffffff;
--search-border-color: #ccc;
--search-focused-color: #0f0fbb;
--search-button-color: #bd0404;
--search-button-hover-color: #bd0404;
--shadow-color: #0000001a;
--item-text-color: #0f0fbb;
--item-number-color: #000000;
--unit-text-color: #bd0404;
--list-background-color: #ffffff;
--list-border-color: #ccc;
--spinner-color: #0000001a;
--spinner-accent-color: #3437db; -->

<script lang="ts">
  import { onMount } from "svelte";

  interface nluObject {
    NLU: number;
    Description: string;
    Article: number;
    Unit: string;
  }

  // const theme = {
  //   "--background-color": "#eedacc;",
  //   "--search-background-color": "#ffffff;",
  //   "--search-border-color": "#ccc;",
  //   "--search-focused-color": "#0f0fbb;",
  //   "--search-button-color": "#bd0404;",
  //   "--search-button-hover-color": "#bd0404;",
  //   "--shadow-color": "#0000001a;",
  //   "--item-text-color": "#0f0fbb;",
  //   "--item-number-color": "#000000;",
  //   "--unit-text-color": "#bd0404;",
  //   "--list-background-color": "#ffffff;",
  //   "--list-border-color": "#ccc;",
  //   "--spinner-color": "#0000001a;",
  //   "--spinner-accent-color": "#3437db;",
  // };
  let searchTerm = "";
  let nlus: nluObject[] = [
    { NLU: 1, Description: "Red Grapes", Article: 341876, Unit: "LB" },
    { NLU: 2, Description: "Avocados", Article: 356486, Unit: "EA" },
    { NLU: 3, Description: "Cabbage", Article: 356512, Unit: "LB" },
    { NLU: 4, Description: "Bananas", Article: 262747, Unit: "LB" },
    { NLU: 5, Description: "Cantaloupe", Article: 356522, Unit: "EA" },
    { NLU: 6, Description: "Cucumbers", Article: 356549, Unit: "EA" },
    {
      NLU: 7,
      Description: "Bananas Organic",
      Article: 262770,
      Unit: "LB",
    },
    { NLU: 8, Description: "Green Grapes", Article: 356384, Unit: "LB" },
    { NLU: 9, Description: "Mangoes", Article: 356419, Unit: "EA" },
    {
      NLU: 10,
      Description: "Roma Tomatoes",
      Article: 356615,
      Unit: "LB",
    },
    {
      NLU: 11,
      Description: "Sweet Potatoes",
      Article: 356662,
      Unit: "LB",
    },
    {
      NLU: 12,
      Description: "Iceberg Lettuce",
      Article: 356396,
      Unit: "EA",
    },
    {
      NLU: 13,
      Description: "Seeded Watermelon",
      Article: 356627,
      Unit: "EA",
    },
    { NLU: 14, Description: "Cauliflower", Article: 356526, Unit: "EA" },
    {
      NLU: 15,
      Description: "Seedless Watermelon",
      Article: 356629,
      Unit: "EA",
    },
    { NLU: 16, Description: "Red Onions", Article: 356610, Unit: "LB" },
    { NLU: 17, Description: "Pomegranates", Article: 356596, Unit: "EA" },
    { NLU: 18, Description: "Peaches", Article: 356583, Unit: "LB" },
    {
      NLU: 19,
      Description: "Personal Seedless Watermelon",
      Article: 356598,
      Unit: "EA",
    },
    {
      NLU: 20,
      Description: "Poblano Peppers",
      Article: 356595,
      Unit: "LB",
    },
    { NLU: 21, Description: "Tomatillos", Article: 356672, Unit: "LB" },
    { NLU: 22, Description: "Papayas", Article: 356576, Unit: "LB" },
    {
      NLU: 23,
      Description: "Jalapeno Peppers",
      Article: 356399,
      Unit: "LB",
    },
    { NLU: 25, Description: "Eggplant", Article: 356555, Unit: "LB" },
    {
      NLU: 26,
      Description: "Baking Potatoes",
      Article: 356492,
      Unit: "LB",
    },
    {
      NLU: 27,
      Description: "Evercrisp Apples Tote",
      Article: 356559,
      Unit: "LB",
    },
    {
      NLU: 28,
      Description: "Pazazz Apples Tote",
      Article: 356581,
      Unit: "LB",
    },
    {
      NLU: 29,
      Description: "WildTwist Apples Tote",
      Article: 356684,
      Unit: "LB",
    },
    {
      NLU: 30,
      Description: "Honey Mangoes",
      Article: 356391,
      Unit: "EA",
    },
    { NLU: 31, Description: "White Onions", Article: 356680, Unit: "LB" },
    {
      NLU: 32,
      Description: "Ruby Frost Apples Tote",
      Article: 356618,
      Unit: "LB",
    },
    { NLU: 33, Description: "Dragon Fruit", Article: 356552, Unit: "EA" },
    { NLU: 34, Description: "Red Cherries", Article: 356606, Unit: "LB" },
    {
      NLU: 35,
      Description: "Rainier Cherries",
      Article: 356603,
      Unit: "LB",
    },
    { NLU: 36, Description: "Pumpkins", Article: 356599, Unit: "EA" },
    {
      NLU: 37,
      Description: "Cotton Candy Grapes",
      Article: 356545,
      Unit: "LB",
    },
    { NLU: 38, Description: "Acorn Squash", Article: 356463, Unit: "LB" },
    {
      NLU: 39,
      Description: "Butternut Squash",
      Article: 356510,
      Unit: "LB",
    },
    {
      NLU: 40,
      Description: "Spaghetti Squash",
      Article: 356642,
      Unit: "LB",
    },
    { NLU: 42, Description: "Plantains", Article: 262730, Unit: "EA" },
    { NLU: 43, Description: "Pineapples", Article: 282119, Unit: "EA" },
    {
      NLU: 44,
      Description: "Seedless Cucumbers",
      Article: 356628,
      Unit: "EA",
    },
    { NLU: 45, Description: "Avocados", Article: 356485, Unit: "EA" },
    {
      NLU: 46,
      Description: "Russet Potatoes 10lb",
      Article: 356619,
      Unit: "EA",
    },
    { NLU: 47, Description: "Grapefruit", Article: 356379, Unit: "EA" },
    {
      NLU: 48,
      Description: "Chayote Squash",
      Article: 356528,
      Unit: "EA",
    },
    {
      NLU: 49,
      Description: "Calabaza Squash",
      Article: 356516,
      Unit: "LB",
    },
    { NLU: 51, Description: "Limes", Article: 356413, Unit: "EA" },
    {
      NLU: 52,
      Description: "Peppers Anaheim",
      Article: 356586,
      Unit: "LB",
    },
    {
      NLU: 53,
      Description: "Athena Cantaloupe",
      Article: 356478,
      Unit: "EA",
    },
    { NLU: 54, Description: "Asparagus", Article: 356476, Unit: "LB" },
    {
      NLU: 55,
      Description: "Envy Apples Tote",
      Article: 537180,
      Unit: "LB",
    },
    {
      NLU: 59,
      Description: "Artisan Lettuce",
      Article: 356473,
      Unit: "EA",
    },
    {
      NLU: 60,
      Description: "Baby Peeled Carrots",
      Article: 356488,
      Unit: "EA",
    },
    {
      NLU: 61,
      Description: "Bagged Mini Avocados",
      Article: 356490,
      Unit: "EA",
    },
    {
      NLU: 62,
      Description: "Beefsteak Tomatoes",
      Article: 356496,
      Unit: "EA",
    },
    {
      NLU: 63,
      Description: "Boston Hydroponic Lettuce",
      Article: 356507,
      Unit: "EA",
    },
    { NLU: 64, Description: "Celery", Article: 356527, Unit: "EA" },
    { NLU: 65, Description: "Cilantro", Article: 356537, Unit: "EA" },
    {
      NLU: 66,
      Description: "Cotton Candy Grapes 1lb",
      Article: 356543,
      Unit: "EA",
    },
    {
      NLU: 67,
      Description: "Grape Tomatoes",
      Article: 356377,
      Unit: "EA",
    },
    {
      NLU: 68,
      Description: "Green Leaf Hydroponic Lettuce",
      Article: 473707,
      Unit: "EA",
    },
    {
      NLU: 69,
      Description: "Green Leaf Lettuce",
      Article: 356385,
      Unit: "EA",
    },
    {
      NLU: 70,
      Description: "Large Baking Potatoes 5lb",
      Article: 356408,
      Unit: "EA",
    },
    { NLU: 71, Description: "Lemons 2lb", Article: 356410, Unit: "EA" },
    {
      NLU: 72,
      Description: "Multi-Colored Peppers",
      Article: 356427,
      Unit: "EA",
    },
    {
      NLU: 73,
      Description: "Ambrosia Apples Tote",
      Article: 356466,
      Unit: "LB",
    },
    {
      NLU: 74,
      Description: "Cosmic Crisp Apples Tote",
      Article: 356542,
      Unit: "LB",
    },
    {
      NLU: 75,
      Description: "Honeycrisp Apples Tote",
      Article: 356394,
      Unit: "LB",
    },
    {
      NLU: 76,
      Description: "Sweetango Apples Tote",
      Article: 356665,
      Unit: "LB",
    },
    {
      NLU: 77,
      Description: "Snapdragon Apples Tote",
      Article: 356637,
      Unit: "LB",
    },
    {
      NLU: 78,
      Description: "Autumn Glory Apples Tote",
      Article: 356481,
      Unit: "LB",
    },
    {
      NLU: 79,
      Description: "Jazz Apples Tote",
      Article: 356401,
      Unit: "LB",
    },
    { NLU: 80, Description: "Envy Apples", Article: 356558, Unit: "LB" },
    { NLU: 82, Description: "Gala Apples", Article: 356369, Unit: "LB" },
    {
      NLU: 84,
      Description: "Honeycrisp Apples",
      Article: 356393,
      Unit: "LB",
    },
    {
      NLU: 85,
      Description: "Blanca Malanga",
      Article: 356503,
      Unit: "LB",
    },
    { NLU: 86, Description: "Honeydew", Article: 356395, Unit: "EA" },
    { NLU: 87, Description: "Jicama", Article: 356402, Unit: "LB" },
    {
      NLU: 88,
      Description: "Large Russet Potato",
      Article: 457522,
      Unit: "LB",
    },
    { NLU: 89, Description: "Name", Article: 356429, Unit: "LB" },
    { NLU: 90, Description: "Yuca", Article: 356690, Unit: "LB" },
    {
      NLU: 91,
      Description: "Scoop Cat Litter w Baking Soda",
      Article: 367175,
      Unit: "EA",
    },
    { NLU: 92, Description: "Salt Pellets", Article: 399026, Unit: "EA" },
    {
      NLU: 93,
      Description: "Complete Nutrition Dry Dog Food",
      Article: 365210,
      Unit: "EA",
    },
    {
      NLU: 94,
      Description: "Complete Nutrition Dry Cat Food",
      Article: 365197,
      Unit: "EA",
    },
    {
      NLU: 95,
      Description: "Flavored Water 24pk",
      Article: 382213,
      Unit: "EA",
    },
    { NLU: 96, Description: "Nectarines", Article: 557838, Unit: "LB" },
    {
      NLU: 97,
      Description: "Purified Water 10oz 24pk",
      Article: 382211,
      Unit: "EA",
    },
    {
      NLU: 98,
      Description: "Natural Spring Water",
      Article: 382135,
      Unit: "EA",
    },
    {
      NLU: 99,
      Description: "Purified Drinking Water",
      Article: 382630,
      Unit: "EA",
    },
    { NLU: 100, Description: "Plums Loose", Article: 569581, Unit: "LB" },
    {
      NLU: 101,
      Description: "US Bottle Deposit 2c (returns)",
      Article: 80000623,
      Unit: "EA",
    },
    {
      NLU: 102,
      Description: "US Bottle Deposit 5c (returns)",
      Article: 80000625,
      Unit: "EA",
    },
    {
      NLU: 103,
      Description: "US Bottle Deposit 10c (returns)",
      Article: 80000627,
      Unit: "EA",
    },
    {
      NLU: 104,
      Description: "US Bottle Deposit 12c (returns)",
      Article: 80000629,
      Unit: "EA",
    },
    {
      NLU: 105,
      Description: "US Bottle Deposit 15c (returns)",
      Article: 80000631,
      Unit: "EA",
    },
    {
      NLU: 107,
      Description: "Broccoli Organic",
      Article: 356446,
      Unit: "EA",
    },
    {
      NLU: 108,
      Description: "Celery Hearts Organic",
      Article: 356448,
      Unit: "EA",
    },
    {
      NLU: 109,
      Description: "Mini Cucumbers Organic",
      Article: 356459,
      Unit: "EA",
    },
    { NLU: 110, Description: "Parsley", Article: 356578, Unit: "EA" },
    {
      NLU: 111,
      Description: "Red Onions 2lb",
      Article: 356609,
      Unit: "EA",
    },
    {
      NLU: 112,
      Description: "Red Potatoes 5lb",
      Article: 356612,
      Unit: "EA",
    },
    {
      NLU: 113,
      Description: "Sweet Onions 2lb",
      Article: 356659,
      Unit: "EA",
    },
    {
      NLU: 114,
      Description: "Sweet Potatoes 3lb",
      Article: 356661,
      Unit: "EA",
    },
    {
      NLU: 115,
      Description: "White Onions 2lb",
      Article: 356679,
      Unit: "EA",
    },
    {
      NLU: 116,
      Description: "Yellow Onions 3lb",
      Article: 341878,
      Unit: "EA",
    },
  ];
  let filteredNlus: nluObject[] = [
    { NLU: 1, Description: "Red Grapes", Article: 341876, Unit: "LB" },
    { NLU: 2, Description: "Avocados", Article: 356486, Unit: "EA" },
    { NLU: 3, Description: "Cabbage", Article: 356512, Unit: "LB" },
    { NLU: 4, Description: "Bananas", Article: 262747, Unit: "LB" },
    { NLU: 5, Description: "Cantaloupe", Article: 356522, Unit: "EA" },
    { NLU: 6, Description: "Cucumbers", Article: 356549, Unit: "EA" },
    {
      NLU: 7,
      Description: "Bananas Organic",
      Article: 262770,
      Unit: "LB",
    },
    { NLU: 8, Description: "Green Grapes", Article: 356384, Unit: "LB" },
    { NLU: 9, Description: "Mangoes", Article: 356419, Unit: "EA" },
    {
      NLU: 10,
      Description: "Roma Tomatoes",
      Article: 356615,
      Unit: "LB",
    },
    {
      NLU: 11,
      Description: "Sweet Potatoes",
      Article: 356662,
      Unit: "LB",
    },
    {
      NLU: 12,
      Description: "Iceberg Lettuce",
      Article: 356396,
      Unit: "EA",
    },
    {
      NLU: 13,
      Description: "Seeded Watermelon",
      Article: 356627,
      Unit: "EA",
    },
    { NLU: 14, Description: "Cauliflower", Article: 356526, Unit: "EA" },
    {
      NLU: 15,
      Description: "Seedless Watermelon",
      Article: 356629,
      Unit: "EA",
    },
    { NLU: 16, Description: "Red Onions", Article: 356610, Unit: "LB" },
    { NLU: 17, Description: "Pomegranates", Article: 356596, Unit: "EA" },
    { NLU: 18, Description: "Peaches", Article: 356583, Unit: "LB" },
    {
      NLU: 19,
      Description: "Personal Seedless Watermelon",
      Article: 356598,
      Unit: "EA",
    },
    {
      NLU: 20,
      Description: "Poblano Peppers",
      Article: 356595,
      Unit: "LB",
    },
    { NLU: 21, Description: "Tomatillos", Article: 356672, Unit: "LB" },
    { NLU: 22, Description: "Papayas", Article: 356576, Unit: "LB" },
    {
      NLU: 23,
      Description: "Jalapeno Peppers",
      Article: 356399,
      Unit: "LB",
    },
    { NLU: 25, Description: "Eggplant", Article: 356555, Unit: "LB" },
    {
      NLU: 26,
      Description: "Baking Potatoes",
      Article: 356492,
      Unit: "LB",
    },
    {
      NLU: 27,
      Description: "Evercrisp Apples Tote",
      Article: 356559,
      Unit: "LB",
    },
    {
      NLU: 28,
      Description: "Pazazz Apples Tote",
      Article: 356581,
      Unit: "LB",
    },
    {
      NLU: 29,
      Description: "WildTwist Apples Tote",
      Article: 356684,
      Unit: "LB",
    },
    {
      NLU: 30,
      Description: "Honey Mangoes",
      Article: 356391,
      Unit: "EA",
    },
    { NLU: 31, Description: "White Onions", Article: 356680, Unit: "LB" },
    {
      NLU: 32,
      Description: "Ruby Frost Apples Tote",
      Article: 356618,
      Unit: "LB",
    },
    { NLU: 33, Description: "Dragon Fruit", Article: 356552, Unit: "EA" },
    { NLU: 34, Description: "Red Cherries", Article: 356606, Unit: "LB" },
    {
      NLU: 35,
      Description: "Rainier Cherries",
      Article: 356603,
      Unit: "LB",
    },
    { NLU: 36, Description: "Pumpkins", Article: 356599, Unit: "EA" },
    {
      NLU: 37,
      Description: "Cotton Candy Grapes",
      Article: 356545,
      Unit: "LB",
    },
    { NLU: 38, Description: "Acorn Squash", Article: 356463, Unit: "LB" },
    {
      NLU: 39,
      Description: "Butternut Squash",
      Article: 356510,
      Unit: "LB",
    },
    {
      NLU: 40,
      Description: "Spaghetti Squash",
      Article: 356642,
      Unit: "LB",
    },
    { NLU: 42, Description: "Plantains", Article: 262730, Unit: "EA" },
    { NLU: 43, Description: "Pineapples", Article: 282119, Unit: "EA" },
    {
      NLU: 44,
      Description: "Seedless Cucumbers",
      Article: 356628,
      Unit: "EA",
    },
    { NLU: 45, Description: "Avocados", Article: 356485, Unit: "EA" },
    {
      NLU: 46,
      Description: "Russet Potatoes 10lb",
      Article: 356619,
      Unit: "EA",
    },
    { NLU: 47, Description: "Grapefruit", Article: 356379, Unit: "EA" },
    {
      NLU: 48,
      Description: "Chayote Squash",
      Article: 356528,
      Unit: "EA",
    },
    {
      NLU: 49,
      Description: "Calabaza Squash",
      Article: 356516,
      Unit: "LB",
    },
    { NLU: 51, Description: "Limes", Article: 356413, Unit: "EA" },
    {
      NLU: 52,
      Description: "Peppers Anaheim",
      Article: 356586,
      Unit: "LB",
    },
    {
      NLU: 53,
      Description: "Athena Cantaloupe",
      Article: 356478,
      Unit: "EA",
    },
    { NLU: 54, Description: "Asparagus", Article: 356476, Unit: "LB" },
    {
      NLU: 55,
      Description: "Envy Apples Tote",
      Article: 537180,
      Unit: "LB",
    },
    {
      NLU: 59,
      Description: "Artisan Lettuce",
      Article: 356473,
      Unit: "EA",
    },
    {
      NLU: 60,
      Description: "Baby Peeled Carrots",
      Article: 356488,
      Unit: "EA",
    },
    {
      NLU: 61,
      Description: "Bagged Mini Avocados",
      Article: 356490,
      Unit: "EA",
    },
    {
      NLU: 62,
      Description: "Beefsteak Tomatoes",
      Article: 356496,
      Unit: "EA",
    },
    {
      NLU: 63,
      Description: "Boston Hydroponic Lettuce",
      Article: 356507,
      Unit: "EA",
    },
    { NLU: 64, Description: "Celery", Article: 356527, Unit: "EA" },
    { NLU: 65, Description: "Cilantro", Article: 356537, Unit: "EA" },
    {
      NLU: 66,
      Description: "Cotton Candy Grapes 1lb",
      Article: 356543,
      Unit: "EA",
    },
    {
      NLU: 67,
      Description: "Grape Tomatoes",
      Article: 356377,
      Unit: "EA",
    },
    {
      NLU: 68,
      Description: "Green Leaf Hydroponic Lettuce",
      Article: 473707,
      Unit: "EA",
    },
    {
      NLU: 69,
      Description: "Green Leaf Lettuce",
      Article: 356385,
      Unit: "EA",
    },
    {
      NLU: 70,
      Description: "Large Baking Potatoes 5lb",
      Article: 356408,
      Unit: "EA",
    },
    { NLU: 71, Description: "Lemons 2lb", Article: 356410, Unit: "EA" },
    {
      NLU: 72,
      Description: "Multi-Colored Peppers",
      Article: 356427,
      Unit: "EA",
    },
    {
      NLU: 73,
      Description: "Ambrosia Apples Tote",
      Article: 356466,
      Unit: "LB",
    },
    {
      NLU: 74,
      Description: "Cosmic Crisp Apples Tote",
      Article: 356542,
      Unit: "LB",
    },
    {
      NLU: 75,
      Description: "Honeycrisp Apples Tote",
      Article: 356394,
      Unit: "LB",
    },
    {
      NLU: 76,
      Description: "Sweetango Apples Tote",
      Article: 356665,
      Unit: "LB",
    },
    {
      NLU: 77,
      Description: "Snapdragon Apples Tote",
      Article: 356637,
      Unit: "LB",
    },
    {
      NLU: 78,
      Description: "Autumn Glory Apples Tote",
      Article: 356481,
      Unit: "LB",
    },
    {
      NLU: 79,
      Description: "Jazz Apples Tote",
      Article: 356401,
      Unit: "LB",
    },
    { NLU: 80, Description: "Envy Apples", Article: 356558, Unit: "LB" },
    { NLU: 82, Description: "Gala Apples", Article: 356369, Unit: "LB" },
    {
      NLU: 84,
      Description: "Honeycrisp Apples",
      Article: 356393,
      Unit: "LB",
    },
    {
      NLU: 85,
      Description: "Blanca Malanga",
      Article: 356503,
      Unit: "LB",
    },
    { NLU: 86, Description: "Honeydew", Article: 356395, Unit: "EA" },
    { NLU: 87, Description: "Jicama", Article: 356402, Unit: "LB" },
    {
      NLU: 88,
      Description: "Large Russet Potato",
      Article: 457522,
      Unit: "LB",
    },
    { NLU: 89, Description: "Name", Article: 356429, Unit: "LB" },
    { NLU: 90, Description: "Yuca", Article: 356690, Unit: "LB" },
    {
      NLU: 91,
      Description: "Scoop Cat Litter w Baking Soda",
      Article: 367175,
      Unit: "EA",
    },
    { NLU: 92, Description: "Salt Pellets", Article: 399026, Unit: "EA" },
    {
      NLU: 93,
      Description: "Complete Nutrition Dry Dog Food",
      Article: 365210,
      Unit: "EA",
    },
    {
      NLU: 94,
      Description: "Complete Nutrition Dry Cat Food",
      Article: 365197,
      Unit: "EA",
    },
    {
      NLU: 95,
      Description: "Flavored Water 24pk",
      Article: 382213,
      Unit: "EA",
    },
    { NLU: 96, Description: "Nectarines", Article: 557838, Unit: "LB" },
    {
      NLU: 97,
      Description: "Purified Water 10oz 24pk",
      Article: 382211,
      Unit: "EA",
    },
    {
      NLU: 98,
      Description: "Natural Spring Water",
      Article: 382135,
      Unit: "EA",
    },
    {
      NLU: 99,
      Description: "Purified Drinking Water",
      Article: 382630,
      Unit: "EA",
    },
    { NLU: 100, Description: "Plums Loose", Article: 569581, Unit: "LB" },
    {
      NLU: 101,
      Description: "US Bottle Deposit 2c (returns)",
      Article: 80000623,
      Unit: "EA",
    },
    {
      NLU: 102,
      Description: "US Bottle Deposit 5c (returns)",
      Article: 80000625,
      Unit: "EA",
    },
    {
      NLU: 103,
      Description: "US Bottle Deposit 10c (returns)",
      Article: 80000627,
      Unit: "EA",
    },
    {
      NLU: 104,
      Description: "US Bottle Deposit 12c (returns)",
      Article: 80000629,
      Unit: "EA",
    },
    {
      NLU: 105,
      Description: "US Bottle Deposit 15c (returns)",
      Article: 80000631,
      Unit: "EA",
    },
    {
      NLU: 107,
      Description: "Broccoli Organic",
      Article: 356446,
      Unit: "EA",
    },
    {
      NLU: 108,
      Description: "Celery Hearts Organic",
      Article: 356448,
      Unit: "EA",
    },
    {
      NLU: 109,
      Description: "Mini Cucumbers Organic",
      Article: 356459,
      Unit: "EA",
    },
    { NLU: 110, Description: "Parsley", Article: 356578, Unit: "EA" },
    {
      NLU: 111,
      Description: "Red Onions 2lb",
      Article: 356609,
      Unit: "EA",
    },
    {
      NLU: 112,
      Description: "Red Potatoes 5lb",
      Article: 356612,
      Unit: "EA",
    },
    {
      NLU: 113,
      Description: "Sweet Onions 2lb",
      Article: 356659,
      Unit: "EA",
    },
    {
      NLU: 114,
      Description: "Sweet Potatoes 3lb",
      Article: 356661,
      Unit: "EA",
    },
    {
      NLU: 115,
      Description: "White Onions 2lb",
      Article: 356679,
      Unit: "EA",
    },
    {
      NLU: 116,
      Description: "Yellow Onions 3lb",
      Article: 341878,
      Unit: "EA",
    },
  ];
  // onMount(async () => {
  //   const response = await fetch("/nlus.json");
  //   nlus = await response.json();
  //   filteredNlus = nlus;
  // });

  function clearSearch() {
    searchTerm = "";
    filteredNlus = nlus;
  }

  function handleFormInput() {
    const term = searchTerm.toLowerCase();
    filteredNlus = nlus.filter((nlu) =>
      nlu.Description.toLowerCase().includes(term)
    );
  }
</script>

<!-- // ----------------------------------------------------------------------->

<div class="container">
  <div class="searchBox">
    <input
      bind:value={searchTerm}
      on:input={handleFormInput}
      placeholder="search the list..."
    />
    <button class="clearButton" on:click={clearSearch}>X</button>
  </div>

  {#if filteredNlus.length > 0}
    <ul class="nlu-list">
      {#each filteredNlus as i}
        <li class="nlu-list-item">
          <span class="nlu-description">{i.Description}</span>
          <span class="nlu-number">{i.NLU}</span>
          <span class="nlu-article">{i.Article}</span>
          <span class="nlu-unit">
            {#if i.Unit.includes("LB")}LRW{/if}
            {#if i.Unit.includes("EA")}each{/if}</span
          >
        </li>
      {/each}
    </ul>
  {:else}
    <!-- Loading spinner -->
    <div class="spinner"></div>
  {/if}
</div>

<!-- // ----------------------------------------------------------------------->

<style>
  @import url("https://fonts.googleapis.com/css2?family=Gentium+Book+Plus:ital,wght@0,400;0,700;1,400;1,700&family=Noto+Sans:ital,wght@0,100..900;1,100..900&family=Roboto+Mono:ital,wght@0,100..700;1,100..700&display=swap");

  :root {
    --background-color: #eee0e0;
    --search-background-color: #e7e7e7;
    --search-border-color: #bd93bd;
    --search-focused-color: #bd93bd;
    --search-button-color: #f05365;
    --search-button-hover-color: #ca2b3e;
    --shadow-color: #0000001a;
    --item-text-color: #000000;
    --item-number-color: #000000;
    --unit-text-color: #533a00;
    --list-background-color: #f2edeb;
    --list-border-color: #f05365;
    --spinner-color: #0000001a;
    --spinner-accent-color: #3437db;
    background-color: var(--background-color);
  }

  .container {
    max-width: 720px;
    margin: 0 auto;
    padding: 1rem;
  }

  .nlu-description {
    color: var(--item-text-color);
    font-family: "Noto Sans", monospace;
    font-size: 1.2rem;
    margin-right: 8px;
  }

  .nlu-article {
    color: var(--item-number-color);
    font-family: "Gentium Book Plus", monospace;
    font-size: 1rem;
    margin-right: 8px;
  }

  .nlu-number {
    color: var(--item-number-color);
    font-family: "Roboto Mono", sans-serif;
    font-size: 1.6rem;
    margin-left: 8px;
    margin-right: 16px;
  }

  .nlu-unit {
    color: var(--unit-text-color);
    font-size: 1rem;
    font-family: "Gentium Book Plus", serif;
  }

  .searchBox {
    display: flex;
    align-items: center;
    margin-bottom: 1rem;
    padding: 0.5rem;
    background-color: var(--search-background-color);
    border: 1px solid #ccc;
    border-radius: 8px;
    box-shadow: 0 2px 4px #0000001a;
  }

  .searchBox input {
    flex: 1;
    padding: 0.5rem;
    font-size: 1rem;
    border: 1px solid #ccc;
    border-radius: 4px;
    margin-right: 0.5rem;
  }

  .searchBox input:focus {
    outline: none;
    border-color: var(--search-focused-color);
  }

  .searchBox button {
    padding: 0.5rem 1rem;
    font-size: 1rem;
    border: none;
    background-color: var(--search-button-color);
    color: white;
    border-radius: 4px;
    cursor: pointer;
    transition: background-color 0.3s;
  }

  .searchBox button:hover {
    background-color: var(--search-button-hover-color);
  }

  .nlu-list {
    list-style-type: none;
    padding: 0;
    margin: 0;
  }

  .nlu-list-item {
    display: flex;
    align-items: center;
    padding: 0.5rem;
    margin: 0 auto;
    max-width: 70%;
    margin-bottom: 0.5rem;
    background-color: var(--list-background-color);
    border: 1px solid var(--list-border-color);
    border-radius: 8px;
    box-shadow: 0 2px 4px var(--shadow-color);
  }

  .nlu-item:last-child {
    margin-bottom: 0;
  }

  .spinner {
    border: 5px solid var(--spinner-color);
    border-top: 5px solid var(--spinner-accent-color);
    border-radius: 50%;
    width: 50px;
    height: 50px;
    animation: spin 1s linear infinite;
    margin: auto;
    margin-top: 50px;
  }

  @keyframes spin {
    0% {
      transform: rotate(0deg);
    }
    100% {
      transform: rotate(360deg);
    }
  }
</style>
