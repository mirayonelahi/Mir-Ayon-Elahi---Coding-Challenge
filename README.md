# Work / Project Examples

## Tug of Logic: TypeScript | React | Redux | Node | RedisDB

● Developed a social reasoning game for a client which is currently used by douglas college students. <br/>
● Worked directly with client to establish project scope, interaction guidelines and project timelines.<br/>
● Build robust and scalable web API using SocketIO, Express and Redis DB.<br/>
● Source with full explained documentation https://github.com/mirayonelahi/TugOfLogic <br/>
● Demonstration of the project https://www.youtube.com/watch?v=wQxHfl3zA04&t=626s <br/>

## Barbershop App: Python | Flask | REST API | MongoDB | AWS

● Developed a barbershop application and deployed using AWS and REST API. <br/>
● Implemented email notification messaging service using Amazon Simple Notification Service (SNS). <br/>
● Prepared documentation with Microsoft Excel, Microsoft Word. <br/>

## Portfolio Website: React | GraphQL | Sanity

● Designed a unique and simplified developer portfolio site to showcase all my projects and blogs <br/>
where sanity used for changing the content dynamically. <br/>
● Link: https://www.mirayonelahi.me/ <br/>
● Source: https://github.com/mirayonelahi/portfolio-sanity-react

# Inspiration:

## Be My Eyes - https://www.bemyeyes.com/

● This is a app where any blind people can request for help by video call and any volunteer can pick up the call and help that blind person. <br/>
● This unique idea really inspired me to create something similar where i can create something similar and people helping each other. <br/>

## CodinGame - https://www.codingame.com/start

● This is a site where you can play games by coding. <br/>
● I always wanted to create something like this and inspired me to create a game where you can solve puzzle in interactive game by coding. <br/>

## Scrimba - https://scrimba.com/dashboard

● This is a online platform where you can learn programming by watching tutorial and interesting thing is that you can pause the video and start coding directly in the screencast. <br/>
● I always wanted to write code while watching any tutorial directly in same screen without any other setup and this idea and implementation really fascinated me. <br/>

# Focus

I will be starting learning more deep in Three.js and make a 3D application and host it on using AWS. My main focus will be building a full stack app and also becoming expert using different AWS technologies. I will also be learning and implementing industry best practices, unit test, integration test, CI/CD. All will be done by hands on building real time application and by this i will get more confidence to build any app.

# Code Challenge

Codesandbox implementation link : https://codesandbox.io/s/2022-internship-exercise-menu-forked-2lqdwi

## Code Explanation:

- I used React and TailwindCSS to implement the menu.
- First by looking at the dataset given and requirement we design our react components.
- We will use 3 different components to implement the menu. These components are parent to child heirarchy.
  - App (This is the main component which will be the parent of all other components.)
  - Menu (Here all the category will be rendered)
  - MenuItem (Here all the single menu will be rendered)

```js
const items = menu.items;
const categories = [...new Set(items.map((menu) => menu.type))].sort((a, b) =>
  b.localeCompare(a)
);
```

- we import the data set and its given as array of objects.
- then from the data set the unique category will be created and sorted in descending order.

`const [spicyOn, setSpicyOn] = useState(true);`

- we create a useState hook to toggle the spicy menu and get track of the spicy menu state.

````js
  <div className="flex justify-center">
          {setSpicyOn ? "Show" : "Hide"} Spicy?
          <div className="hover:bg-gray-100 rounded-md px-1 ">
            {spicyOn ? (
              <AiFillFire onClick={() => setSpicyOn(!spicyOn)} size={25} />
            ) : (
              <AiOutlineFire onClick={() => setSpicyOn(!spicyOn)} size={25} />
            )}
          </div>
        </div>
        ```
````

- Here we are showing dynamic value using the created hook and also showing different icons based on the spicy menu state.

````js
  {categories.map((category) => {
          let cItems = items
            .filter((item) => item.type === category)
            .sort((a, b) => a.menuOrder - b.menuOrder);
          if (!spicyOn) cItems = cItems.filter((items) => !items.spicy);
          return <Menu key={category} items={cItems} cateogryName={category}  />;
        })}
        ```
````

- In here one of our main functionality is handled.
- Firstly depending on the categories we filter the data and sort as oer the menu order as per the requirement.
- Depending on the spicy toggle button we are sending data with spicy menu or without spicy menu.
- Category name and category items are passed as props to the Menu component.

```js
const Menu = ({ items, cateogryName }) => {
  return (
    <div className="rounded-md shadow-md p-5  ">
      {!items && <p>Loading</p>}
      <div className="text-2xl pb-2 font-semibold text-center capitalize">
        {cateogryName}
      </div>
      {items.map((item) => (
        <MenuItem key={item.name} item={item} />
      ))}
    </div>
  );
};
```

- Now in Menu component we are getting items and category name as props.
- And from here we are mapping the items are passing each item as props to the MenuItem component.

```js
const MenuItem = ({ item }) => {
  return (
    <div
      className={
        item.spicy
          ? `p-4 border-2 border-red-400 rounded-lg shadow-lg hover:bg-red-100`
          : "p-4 border-1 rounded-lg shadow-lg hover:bg-green-100"
      }
    >
      <div className="flex justify-between py-2">
        <h4 className="text-xl">{item.name} </h4>
        <div className="text-xl font-semibold">${item.price.toFixed(2)}</div>
      </div>
      <div className="italic">{item.description}</div>
      <div className="flex justify-center">
        {item.spicy && <AiFillFire size={25} />}
      </div>
    </div>
  );
};
```

- Here each single item is rendered and shown in the menu.
- For price we are formatting it according to the requirement.
- Depending on the toggle button we are showing the spicy menu or not.
- For spicy menu we implemented different design.
