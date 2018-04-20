```jsx
class Person {
	constructor(name = 'Anonymous', age = 0) {
		this.name = name;
		this.age = age;
	}
	getGreeting() {
		return `Hi, I am ${this.name}!`;
	}
	getDescription() {
		return `${this.name} is ${this.age} year(s) old.`;
	}
}

class Student extends Person {
  /*-------------------
  	Don't need to set default value for name and age again
  -------------------*/
	constructor(name, age, major) {
		super(name, age);
		this.major = major;
	}
	hasMajor() {
	  /*-------------------
    	Convert a string to boolean
    -------------------*/
		return !!this.major;
	}
	/*-------------------
  	Override parent's getDescription()
  -------------------*/
	getDescription() {
		let description = super.getDescription();
		if (this.hasMajor()) {
			description += ` Their major is ${this.major}.`;
		}
		return description;
	}
}

const me = new Student('Peter Che', 20, 'CS');
console.log(me.getDescription());

const other = new Student(); // Student(undefined, undefined, 'ME')
console.log(other.getDescription());
```