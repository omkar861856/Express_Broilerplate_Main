# Commands - 
  git clone <url> .
  npm install
  Create .env file And store PORT and MONGO_URL there.






# git cheat sheet link - 
    https://education.github.com/git-cheat-sheet-education.pdf

# Login - Signup routes

1) app.post("/signup", async (req, res) => {try {
    const { username, email, password } = req.body;
    const existingUser = await collection.findOne({ email });

    if (existingUser) {
      return res
        .status(400)
        .send("User already exists selecet another email id");
    }

    //hash

    const saltRounds = parseInt(process.env.SALT);

    const hashedPassword = bcrypt.hash(
      password,
      saltRounds,
      async (err, hash) => {
        if (err) throw err;

        const result = await collection.insertOne({
          username,
          email,
          password: hash,
        });

        res.status(201).send("Successfully registered");
      }
    )} catch (error) {
    console.log(error);
    res.send(error);
  }});

2) app.post("/login", async (req, res) => {try {
    const { email, password } = req.body;

    const user = await collection.findOne({ email });

    if (!user) {
      return res.status(404).send("User not found");
    }

    const match = await bcrypt.compare(password, user.password);

    if (match) {
      res.send("Logged in successfully");
    } else {
      return res.status(401).send("Invalid credentials");
    }}catch (error) {
    console.log(error);
    res.send(error);
  }});
  
