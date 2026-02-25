-- Simple Script Hub (English + Lua)

local hub = {}
hub.scripts = {
    {name = "Example Script", url = "https://raw.githubusercontent.com/yourname/repo/main/script.lua"},
    {name = "Another Script", url = "https://raw.githubusercontent.com/yourname/repo/main/another.lua"}
}

function hub:loadScript(url)
    local response = HttpGet(url)
    if response then
        loadstring(response)()
    else
        print("Failed to load script.")
    end
end

function hub:open()
    print("=== My Script Hub ===")
    for i, script in ipairs(self.scripts) do
        print(i .. ". " .. script.name)
    end
end

function hub:run(index)
    local script = self.scripts[index]
    if script then
        print("Running: " .. script.name)
        self:loadScript(script.url)
    else
        print("Invalid script index.")
    end
end

return hub
  
