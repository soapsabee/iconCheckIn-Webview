<script context="module">
	import {
		Card,
		CardText,
		CardActions,
		Button,
		Icon,
		TextField,
		Container,
		Row,
		Col,
	} from "svelte-materialify";
	
	import { api } from '../lib/api'




	const checkIn = async () => {
		const res = await api("post", `test`,{
			type:"check-in"
		})
	}


	const checkOut = async () => {
		const res = await api("post", `test`,{
			type:"check-out"
		})
	}


	const logOut = () => {

	}

</script>

<!-- <svelte:head>
	<title>About</title>
</svelte:head> -->

<section>
	<Container style="max-width:300px;">
		<div  style="border: solid;" class="mt-10">
			<Row>
				<Col class="d-flex justify-center">
					<h4>ลงเวลา</h4>
				</Col>
			</Row>
			<Row>
				<Col class="d-flex justify-center">
					<Card outlined style="max-width:300px;">
						<div class="d-flex justify-center">
							<CardActions>
								<Button
									rounded
									outlined
									on:click={() => checkIn()}>Check IN</Button
								>
							</CardActions>
							<br />
						</div>
					</Card>
				</Col>
			</Row>
			<Row>
				<Col class="d-flex justify-center">
					<Card outlined style="max-width:300px;">
						<div class="d-flex justify-center">
							<CardActions>
								<Button
									rounded
									outlined
									on:click={() => checkOut()}>Check OUT</Button
								>
							</CardActions>

							<br />
						</div>
					</Card>
				</Col>
			</Row>
			<Row>
				<Col class="d-flex justify-center">
					<Card outlined style="max-width:300px;">
						<div class="d-flex justify-center">
							<CardActions>
								<Button
									rounded
									outlined
									on:click={() => logOut()}>Logout</Button
								>
							</CardActions>

							<br />
						</div>
					</Card>
				</Col>
			</Row>
		</div>
	</Container>
</section>

<style>
</style>
