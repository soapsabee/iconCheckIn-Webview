<!-- <script context="module">
	export const prerender = true;
</script> -->
<script>
	import {
		Card,
		CardText,
		CardActions,
		Button,
		Icon,
		TextField,
	} from "svelte-materialify";
	import { mdiEyeOff, mdiEye } from "@mdi/js";
	import { username, password } from "../lib/store";
	import { goto } from '$app/navigation';

	let show = false;

	const handleInput = (e) => {
		let val = e.value.target.value;
		if (e.key === "username") {
			return username.set(val);
		}

		return password.set(val);
	};

	const login = (e) => {
		username.subscribe((value) => {
			console.log("username: ", value);
		});

		password.subscribe((value) => {
			console.log("password: ", value);
		});
		goto('./about', { replaceState : false, noscroll : true, keepfocus : false, state : {} })
	};
</script>

<!-- 
<svelte:head>
	<title>Home</title>
</svelte:head> -->

<section>
	<div class="d-flex justify-center mt-4 mb-5">
		<Card outlined style="max-width:300px;">
			<div class="pl-4 pr-4 pt-3">
				<span class="text-h5 mb-2">เข้าสู่ระบบ</span>
				<br />
			</div>
			<CardText>
				<TextField
					on:change={(e) =>
						handleInput({ key: "username", value: e })}
					>Username</TextField
				>
				<br />
				<TextField
					on:change={(e) =>
						handleInput({ key: "password", value: e })}
					type={show ? "text" : "password"}
				>
					Password
					<div
						slot="append"
						on:click={() => {
							show = !show;
						}}
					>
						<Icon path={show ? mdiEyeOff : mdiEye} />
					</div>
				</TextField>
			</CardText>
			<CardActions>
				<Button rounded outlined on:click={() => login()}>Login</Button>
			</CardActions>
		</Card>
	</div>
</section>

<style>
</style>
