class: center, middle

# Software licensing and open source explained with cakes

---

<img src="img/cake-1.svg" style="width: 15%;"/>

- Imagine you compose a recipe for a really tasty cake (a great idea).
- In regular intervals you distribute cakes (release binaries).
- Your family and friends love it.
- But you can only bake so many.

(cake emoji licensed under CC-BY-SA-4.0, attribution: [EmojiOne](https://www.emojione.com))

<!--- Perhaps may be worth saying that this is a metaphor - the
ingredients list and basic instructions simply facts, so not
protectable.  However, your description *is* protectable. -->

---

## Possible outcomes 0/4: closed

### Closed source (recipe never released)

- Your cake is celebrated by The New Yorker magazine.
- People will have difficulties to reproduce your celebrated recipe.
- Nobody else will improve your recipe.
- Bad copycats might appear, you don't get any credit.
- Fewer tasty cakes will get consumed.

---

## A friend tells you: why not distribute the recipe?

- Put your recipe on GitHub.
- Start the OpenCake organization.
- Get feedback / start a mailing list.
- More people will be able to enjoy the cake (.emph[increase impact]).
- Maybe somebody will find ways to improve the recipe.
- Everyone will know that it was your idea even though somebody else bakes it.

---

## Mrs. X (running a famous restaurant) finds your cake recipe on GitHub

<img src="img/cake-1.svg" style="width: 15%;"/>

- The chef tries it and it is great.
- The chef suggests improvements (derivative work):

<img src="img/cake-2.svg" style="width: 15%;"/>

- It becomes part of the restaurant menu.
- Or does it? .emph[Depends on your license!]

<!--- What is most important is *how are the changes handled*.  Since
you are giving the recipe out yourself, people can use it "personally"
however they want.  But if they want to improve/reuse/redistribute it,
then what?  -->

---

## Possible outcomes 1/4: custom

### No license or custom license

- No restaurant chef will touch it: too much hassle to employ a lawyer to be sure
  that the cake can be served to customers.
- But maybe they will bake it and eat it and not distribute it and that is OK
  ("fair use" provision permits the making of copies for own use).

<!--- The restaurant industry is infamous for copying recipes and there are
very few published court cases. Let's skim over this fact and stay in the
fictitious example though. -->

---

## Possible outcomes 2/4: permissive

### License: MIT or Apache or BSD-2

- It is OK to use the recipe and sell the cake.
- It is OK to not share the improved recipe.
- If somebody becomes sick, it is not the fault of the OpenCake organization (limit of liability).
- You may not get the improvements back to use yourself.

### License: BSD-3

- In addition to the above it is understood that the updated recipe are not endorsed by the OpenCake organization.

---

## Possible outcomes 3/4: share-alike

### License: GNU Lesser GPL (LGPL)

- The famous restaurant has to share only the improved cake recipe but can keep the rest of the menu closed.
- The restaurant guests have to be able to exchange the cake from the menu by improved cakes from other restaurants (dynamic relinking).

### License: Mozilla Public License v2.0

- Like LGPL but do not require that the modified cake can be exchanged by the restaurant guest.

---

## Possible outcomes 4/4: viral

### License: GNU GPL or GNU Affero GPL

- If the cake is a part of the menu, the famous restaurant has to
  .emph[share the recipes of the entire menu].
- You can use their improved recipe and improve it further:

<img src="img/cake-2.svg" style="width: 15%;"/>
<img src="img/cake-3.svg" style="width: 15%;"/>

- Other restaurants can then reuse and improve the full menu and the hope is that we will all eat better food.
- You support open restaurants. You can use everything they do, too.

<!--- Example of benefits of virality in software: Linksys routers and
GPL's kernel image. Some company used linux, didn't distribute source.
They were fourced to distribute it, and that has directly led to
a huge community of firmware modders.  -->

---

## What outcomes did we have?

### 1. Custom/closed

- **Derivative work typically not possible**: others have to reimplement the wheel

### 2. Permissive

- You may lose access to **derivative work**
- Attractive for companies with proprietary software

### 3. Share-alike

- You can reuse **derivative work**
- Compatible with proprietary software

### 4. Viral

- .emph[You always have access if someone improves and re-shares]
- Not attractive for companies with proprietary software
