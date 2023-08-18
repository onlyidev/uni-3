/*
```javascript
*/
const PI = Math.PI;
const e = Math.exp(1);
const functions = {
	"sin": {
		f: Math.sin,
		lb: "0",
		ub: "PI*2"
	},
	"cos": {
		f: Math.cos,
		lb: "0",
		ub: "PI*2"
	},
	"exp": {
		f: Math.exp,
		lb: "-10",
		ub: "1.5"	
	},
	"sqrt": {
		f: Math.sqrt,
		lb: "0",
		ub: "10"
	},
	"log": {
		f: Math.log,
		lb: "0",
		ub: "10"
	},
	"bell": {
		f: (x) => Math.pow(e,-x*x),
		lb: "-3",
		ub: "3"
	},
	"xx": {
		f: (x) => x*x,
		lb: "-2",
		ub: "2"
	},
	"xxx": {
		f: (x) => x*x*x,
		lb: "-1.5",
		ub: "1.5"
	},
	"custom": (userFun) => {
		return {
			f: eval(`(x) => ${userFun}`),
			lb: "0",
			ub: "1"
		}
	} 
}

const userFunctionRequest = await utils.inputPrompt("Function");
const fun = functions[userFunctionRequest] ?? functions["custom"](userFunctionRequest);
const LOWER_BOUND = eval(await utils.inputPrompt("Lower bound", "", fun.lb)) ?? 0;
const UPPER_BOUND = eval(await utils.inputPrompt("Upper bound", "", fun.ub)) ?? 1;
const points = new Array(Math.ceil(Math.max(1,UPPER_BOUND-LOWER_BOUND))*100);
for(const [i,value] of points.entries()) {
    const x = LOWER_BOUND + i/100; // Setting resolution
    const originX = ea.targetView.currentPosition.x;
    const originY = ea.targetView.currentPosition.y;
    const x_stretch = 10;
    const y_stretch = 100;
    points[i] = [
        originX + x * x_stretch,
        x > UPPER_BOUND ? null : originY + fun.f(x) * y_stretch * -1
    ]
}

ea.setStrokeSharpness(null)
ea.setView("active");
ea.addLine(points.filter(el => el[1] != null));
ea.addElementsToView();

