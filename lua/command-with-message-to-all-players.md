# Problem
You want to create command (f.ex `/announce <message>`) that sends a message to all players.

FiveM provides a command handler (`RegisterCommand`) and the default chat has events you can trigger for this exact purpose (`chat:addMessage`).

```RegisterCommand(commandName, handler, restricted)``` https://runtime.fivem.net/doc/natives/?_0x5FA79B0F
```chat:addMessage {template, color, multiline, args}``` https://docs.fivem.net/docs/resources/chat/events/chat-addMessage/

# Solution
In a **server script**:
```lua
local adminOnly = true -- if you need the command.announce ace permission to use the command or not
RegisterCommand("announce", function(source, args)
  if #args > 0 then -- check if an argument was passed
    local message = table.concat(args, " ") -- stitch together all the message arguments into the message that was sent
    TriggerClientEvent("chat:addMessage", -1, { -- -1 means send to every connected client!
      args = {
        "Announcement", -- First argument is the name
        message -- Pass the message as text
      },
      color = {255, 0, 0}, -- Make the name red! (RGB)
    })
  else
    -- No message was sent, should we tell them they didn't?
  end
end)
