<template>
    <main>
      <h1>Zoznam ľudí</h1>
      <section class="list">
        <section v-for="person of persons" v-bind:key="person"
        v-bind:class="{'card-container':true,'card':true,'adult':currentYear - person.birthday >= 18 }">
          <article class="info">
            <div class="name">{{person.fname}} {{person.lname}}</div>
            <div class="age">
				<div class="date-birth">
					<span class="year-title">Date of Birth: </span>
					{{person.birthday}}
				</div>
				<div class="current-age">
					<span class="year-title">Age: </span>
					{{currentYear - person.birthday}}
				</div>
			</div>
          </article>
          <footer class="footer-card">
            <span class="btn edit">Edit</span>
            <span class="btn remove">Remove</span>
          </footer>
        </section>
      </section>
    </main>
</template>

<script setup>

let persons = [
		{
			fname: "Magdalena",
			lname: "Mikulova",
			birthday: 22
		},
		{
			fname: "Mirka",
			lname: "Makovicova",
			birthday: 30
		},
		{
			fname: "Hugo",
			lname: "Hugovic",
			birthday: 15
		},
		{
			fname: "Miki",
			lname: "Hric",
			birthday: 19
		},
		{
			fname: "Andrea",
			lname: "Veresova",
			birthday: 40
		},
		{
			fname: "Nora",
			lname: "Mojsejova",
			birthday: 13
		},
	]

let currentDate = new Date();
let currentYear = currentDate.getFullYear();

const replaceBirthday = () => {
	persons.forEach((person) => {
		person.birthday = currentYear - person.birthday;
	});
}

replaceBirthday();


</script>

<style>
	@import url('https://fonts.googleapis.com/css2?family=Oswald:wght@200;300;500;600;700&display=swap');
	body {
		font-size: 10px;	
		font-family: 'Oswald', sans-serif;
		padding: 1rem;
	}
	h1 {
		font-size: 30px;
		text-align: center;
		color: rgb(20, 17, 153);
		text-transform: uppercase;
	}
	main {
		display: flex;
		flex-direction: column;
		gap: .75rem;
	}
	.list {
		display: flex;
		gap: 20px;
		flex-direction: row;
		flex-wrap: wrap;
		justify-content: stretch;
		font-size: 1.2rem;
	}
	.card-container {
		flex-grow: 1;
	}
	.card {
		background: rgb(40, 223, 193);
		border: 1px solid #bbb;
		color: #444;
		box-shadow: 0 3px 5px rgba(0,0,0,.2);
		border-top-width: 5px;
		border-top-color: rgb(17, 71, 126);
		border-radius: 10px;
	}
	.card.adult {
		border-top-color: rgb(221, 151, 22);
	}
	.card:hover {
		position: relative;
		left: 5px;
		top: 5px;
		box-shadow: -5px -5px 8px 3px rgba(0,0,0,.2);
	}
	.info {
		padding: 1rem;
		text-align: center;
		font-size: 1.3rem;
	}
	.name {
		font-family: 'Comic Sans MS', sans-serif;
	}
	.age {
		font-weight: 300;
		font-size: 1rem;
	}
	.year-title {
		color: #969393;
	}
	.footer-card {
		display: flex;
	}
	.btn {
		padding: .75rem 2rem;
		color: white;
		width: 50px;
		flex-grow: 1;
		text-align: center;
		transition: .5s;
		font-size: 1rem;
		border-radius: 3px;
	}
	.btn.edit {
		background: rgb(44, 158, 44);
	}
	.btn.remove {
		background: rgb(187, 20, 20);
	}
	.btn:hover {
		opacity: 0.87;
		color: black;
		text-shadow: 1px 1px 2px black;
		cursor: pointer;
	}
</style>

