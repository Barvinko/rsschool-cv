# [rsschool-cv](https://barvinko.github.io/)
![I](/assets/img/Vlad.jpg )
# Vladyslav Barvinko
## CONTACTS
**Phone(Telegram, Viber):** +38 (093) 076 3429 
**Email:** vlad.barvinko@gmail.com
**GitHub:** [https://github.com/Barvinko](https://github.com/Barvinko)
**Linkedin:** [https://www.linkedin.com/in/vlad-barvinko-a445851a9](https://www.linkedin.com/in/vlad-barvinko-a445851a9)
## SKILLS
HTML/CSS/SASS
Bootstrap5
JS/TS(basic)/React(basic)
WebPack
Node.js/Express
MongoDB/Moongoose
Git
VS Code
#### Languages
Ukrainian, Russian - С2
English - B1
## BRIEFLY ABOUT MY EXPIRIENCE
Highlighted such developed projects:
-   Layout of clothing store using Grid;
-   Algorithm for checking bank cards and TIN;
-   Algorithm for finding location of nearest ATMs to user's from the Privat Bank API;
-   News site with current news from AIP;
-   Searching in text, using regular expression.;
-   Displaying countries, currencies, flags, their neighbors(whose flags were found using algorithm) from dataCountry API, on Vue.js;
-   Tasks of genetic algorithms;
-   Website which implements secure messaging system with encryption on eleptic curves. Was implements secure registration, authorization, unique encryption for each message. I used tech stack on this project:
    -   Node.js;
    -   Express.js;
    -   express-session;
    -   MongoDB;
    -   Mongoose.
## EDUCATION
**Dnipro University of Technology,** Bachelor
FIT, 121-Software Engineering 2021
**University of Customs and Finance,** Master`s degree
FIT, 122-Computer Science 2023
## COURSES
**ORTDnipro**
Beginning of web development and programming
[https://ortdnipro.org/web/](https://ortdnipro.org/web/)
**ORTDnipro**
JavaScript in web-development
[https://ortdnipro.org/js/](https://ortdnipro.org/js/)
**Indigo**
English
[https://indigo-dnepr.com/](https://indigo-dnepr.com/)
**EPAM**
IT Marathon
[https://certificates.epam.com/certificates/b6eb2a1c-f136-455e-a7b1-257767e8303b](https://certificates.epam.com/certificates/b6eb2a1c-f136-455e-a7b1-257767e8303b)
## CODE EXAMPLES
The example implements conversion between distance units with support for metric and imperial systems of measures. By default there are rules for conversion: meters (m), centimeters (cm), inches (in) and feet (ft), and support conversion between any units. Conversion rules are stored in JSON in the form:
```
{`${name unit}`: equivalent,...}
```
It is also possible to expand the list of supported units. As an example, the code adds yard."yard" is added as an example. The input data is sent as JSON file, then it is checked using a regular expression and according to the available units. Example of input data format:
```
[{"distance": {"unit": "km", "value": 1}, "convert_to": "m"},...]
```
### Example
```
(async  function () {
	//loading dada about units from jsons file
	let  units  =  await  fetch('./assets/data/units.json');
	let  json  =  await  fetch('./assets/data/data.json')
	units  =  await  units.json();
	json  =  await  json.json();
	console.log(units,json);

	//Add new unit
	addUnit(units,"yd",91.44)

	//Regular expression
	let  chek  = /(\{"distance":\{"unit":"\w*"\,"value":\d*\}\,"convert_to":"\w*"\})/gm
	json  =  JSON.stringify(json)
	json  =  json.match(chek);
	console.log(json);

	//Create array for answers
	let  featback  =  new  Array();
	for (let  item  of  json) {
		item  =  JSON.parse(item);
		if (!(`${item.distance.unit}`  in  units  ||  !`${item.convert_to}`  in  units) ||  typeof(+item.distance.value) !=  'number') {
			console.log(`this no right`,item);
			continue;
		}

		let  value  =  item.distance.value;
		let  equvivalentFromUnit  =  units[item.distance.unit];
		let  equvalentToUnit  =  units[item.convert_to];

		value  = (equvivalentFromUnit  *  value) /  equvalentToUnit;

		featback.push({
			'unit':  item.convert_to,
			'value':  +value.toFixed(2)
		})

	}

	featback  =  JSON.stringify(featback);
	console.log(featback);
}())
```