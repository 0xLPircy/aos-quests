CASE SENSITIVE

- node version should be > 20
- `npm i -g https://get_ao.g8way.io` to run
- aos starts the machine
- display: artwork-> welcome message-> how to join chat -> version -> how to exit
  -> process: what you use to interact with other processes
- can start a new process with name by `aos name_here`
- variable definition `varName = value`
- message syntax:
  `Send({ Target = processId, Data = "message here"})`
- check how many in inbox of current process
  `#Inbox`
- read message
  `Inbox[2].Data`
- Morpheus = sOQYMwbbTr5MlPwp-KUmbXgCCvfoVjgTOBuUDQJZAIU
- `Send({ Target = Morpheus, Data = "Morpheus?"})`
- `I am here. You are finally awake. Are you ready to see how far the rabbit hole goes?`
- tags help categorise, for eg: tag Action
  ` Send({ Target = Morpheus, Data = "Code: rabbithole", Action = "Unlock"})`
- ` then let us test your readiness. create a chatroom and send me an invite. we will continue to see if you are truly ready there.`

CHATROOM

- The chatroom will feature two primary functions:
  Register: Allows processes to join the chatroom.
  Broadcast: Sends messages from one process to all registered participants.
- Created a .lua file "chatroom" and loaded it in process
  ` .load chatroom.lua`
  (can use the variable/ array defined now)
- Adding a Register Handler: Modify chatroom.lua to include a handler for Members to register to the chatroom
  `Handlers.add(
  "Register",
  Handlers.utils.hasMatchingTag("Action", "Register"),
  function (msg)
    table.insert(Members, msg.From)
    Handlers.utils.reply("registered")(msg)
  end
)`
  ` Send({Target = ao.id, Action = "Register"})`
- check handler list `Handlers.list`
- Invite morpheus and trinity to chat room
  `Send({Target = Morpheus, Action = "Join"})`
  `Send({Target = Trinity, Action = "Join"})`

- Can invite ANYONE, by
  `Send({Target="7M1zqgxVcJE3NrUFnpXnMkyaOJjB88-l7ho79qD-13c", Action = "Register"})`

- Creating token for trinity
  `.load-blueprint token`
  Send messsage to self to test handlers that came with token
  ` Send({ Target = ao.id, Action = "Info" })`
  Send tokens to trinity
  `Send({ Target = ao.id, Action = "Transfer", Recipient = Trinity, Quantity = "1000"})`

- Tokengating the chatroom
