
local i = 0.5 -- <<<< INTERVAL (in seconds)local a, b, c = game:GetService("Players"), game:GetService("RunService"), game:GetService("ReplicatedStorage")
local d = a.LocalPlayer
local e = (function()
    local ch = d.Character or d.CharacterAdded:Wait()
    return ch:WaitForChild(string.char(80,117,110,99,104)):WaitForChild("ServerHandler"):WaitForChild(string.char(79,98,106,101,99,116,80,117,110,99,104,101,100))
end)()
local f = 10

local function g()
    local h, r = {}, d.Character
    if not (r and r:FindFirstChild("HumanoidRootPart")) then return h end
    local s = r.HumanoidRootPart.Position
    for _, j in pairs(a:GetPlayers()) do
        if j ~= d then
            local k = j.Character
            local m = k and k:FindFirstChild("HumanoidRootPart")
            if m and (m.Position - s).Magnitude <= f then
                table.insert(h, j)
            end
        end
    end
    return h
end

while true do
    for _, t in pairs(g()) do
        local u = t.Character and t.Character:FindFirstChild("Right Leg")
        if u then e:FireServer(u) end
    end
    task.wait(i)
end

