# Random-Color-Generator-Project

![Random-Color-Generator-Project](RandomColor.gif)

Random Color Generator Project

State Management
const [typeOfColor, setTypeOfColor] = useState("hex");
const [color, setColor] = useState("#000000");

We used the useState hook to manage two pieces of state:
typeOfColor: Tracks the current color type ("hex" or "rgb").
color: Stores the generated color value.

Utility Functions
function randomColorUtility(length) {
  return Math.floor(Math.random() * length);
}

This function generates a random integer between 0 and length - 1.

Color Generation Functions
function handleCreateRandomHexColor() {
  const hex = "0123456789ABCDEF";
  let hexColor = "#";
  for (let i = 0; i < 6; i++) {
    hexColor += hex[randomColorUtility(hex.length)];
  }
  setColor(hexColor);
}

-handleCreateRandomHexColor generates a random hex color string and updates the color state with it.

function handleCreateRandomRgbColor() {
  const r = randomColorUtility(256);
  const g = randomColorUtility(256);
  const b = randomColorUtility(256);
  setColor(`rgb(${r}, ${g}, ${b})`);
}

-handleCreateRandomRgbColor generates a random RGB color string and updates the color state with it.

useEffect Hook

useEffect(() => {
  if (typeOfColor === "rgb") handleCreateRandomRgbColor();
  else handleCreateRandomHexColor();
}, [typeOfColor]);
The useEffect hook runs the appropriate color generation function whenever typeOfColor changes.
