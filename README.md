# kissprincipleforcoding
The very fundamental principle when it comes to coding - Keep It Simple, Stupid


**Real developers code with KISS** **💋**

[warning: wall-of-text]

Short for “Keep It Simple, Stupid”, or formally “Keep It Simple and Straightforward,” KISS is a principle stating that a system should be constructed in a way so that its components can be easily understood. As a result, future code maintenance will require minimal effort.

To understand this concept better, let’s first take a look:

```jsx
class UserService {
	userRepository: Repository;
	
	constructor (userRepository: Repository) {
		this.userRepository = userRepository;
}

public async createUser(input: UserInput): Promise<boolean> {
	const validUserTypes = ['regular','premium','trial'];
	let user: User;
	switch (input.userType) {
		case 'regular':
			user = new User(input.username);
			break;
		case 'premium':
			user = new User(input.username);
			user.permission = ['readPremiumContent','createContent'];
			break;
		case 'trial';
			user = new User(input.username);
			user.isTrial = true;
			break;
		default:
			throw new ArgumentOutOfRangeException('Invalid user type. Must be one of the following $(validUserTypes.join(',')}');
	}
	return this.userRepository.save(user);
}
```

Looking at this example, there’s zero clarity in what this method does. The codes are repeated with each case with no clear responsibility. Everything is sore to the eye, and even sorer to maintain.

Now look at its simpler version:

```jsx
interface ICreateUserInput {
	createUser: () => User;
}

class BetterUserService {
	
	userRepository: Repository;

	constructor (userRepository: Repository) {
		this.userRepository = userRepository;
	}
	
	public async createUser(input: ICreateUserInput): Promise<boolean> {
		const user = input.CreateUser();
		return this.UserRepository.save(user);
	}
}
```

This version is way easier to read while having only one responsibility to create users using input. It’s also easier to extend if there’s a new user type without changing the createUser method. And of course, no code smell as well.

🪄 It’s pretty easy to give your codes a magic KISS, the only thing you should do is to strive to reduce complexity and keep your coding process transparent, and secure. Here are a few points to note down:

- Ensure your classes has a single responsibility
- Ensure your variable names describes the variable properly
- Ensure your method name translates to the purpose of that method
- Avoid global states and behaviors as much as you can
- Delete instances, methods, or redundant processes within the codebase that are not in use

🐸 Real developers Keep It Simple! Stay tuned for more coding techniques, brought to you by FABA Technology. 💋
