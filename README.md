# Notification System for FiveM

**Description:**  
A modern and efficient standalone notification system for FiveM servers.

---

## Features
- *4 Default Notification Types*
- *Optimized for minimal impact on server performance*
- *Fully Customizable*
- *Progress Bar for durability*
- *Anti-Flooding System*

## Installation
1. **Download** the script from the repository.
2. **Place** the script folder in the `resources` directory.
3. **Add** `ensure byteNotify` to `server.cfg`.
4. **Configure** the settings in `config.lua` to suit your server's preferences.

## Example Usage
Here's an example of how to send a notification:

```lua
-- Client Site
exports["byteNotify"]:notify("your title", "your description", "notification type", notification_length) -- notification_length is in milliseconds

-- Server Site
TriggerClientEvent("ByteDevs:Notify", source, "your title", "your description", "notification type", notification_length) -- notification_length is in milliseconds
```

## ESX Integration
replace the `ESX.ShowNotification` function in the `es_extended\client\functions.lua` file with the following function:

```lua
function ESX.ShowNotification(message, notifyType, length)

    if GetResourceState("byteNotify") ~= "missing" then
        return exports["byteNotify"]:notify("your title", message, notifyType, length)
    end

    print("[^1ERROR^7] ^5ESX Notify^7 is Missing!")
end

```

## QbCore Integration
replace the `QBCore.Functions.Notify` function in the `qb-core/client/functions.lua` file with the following function:

```lua
function QBCore.Functions.Notify(text, texttype, length)
    if type(text) == "table" then
        local ttext = text.text or 'Placeholder'
        local caption = text.caption or 'Placeholder'
        local ttype = textype or 'primary'
        local length = length or 5000

        exports["byteNotify"]:notify(caption, ttext, ttype, length)
    else
        local ttype = textype or 'primary'
        local length = length or 5000

         exports["byteNotify"]:notify("Your Title", text, ttype, length)
    end
end

```

## Support
For any issues or inquiries, please feel free to join our Discord community for assistance.

[Join our Discord](https://dsc.gg/bytedevs)

## Contribution
Want to improve the script or suggest new features? Submit a pull request or open an issue in the GitHub repository.
