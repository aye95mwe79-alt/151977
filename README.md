local player = game.Players.LocalPlayer
local character = player.Character or player.CharacterAdded:Wait()
local humanoid = character:WaitForChild("Humanoid")
local rootPart = character:WaitForChild("HumanoidRootPart")

local flying = false
local speed = 60

local UIS = game:GetService("UserInputService")

UIS.InputBegan:Connect(function(input, gameProcessed)
	if gameProcessed then return end
	
	if input.KeyCode == Enum.KeyCode.F then
		flying = not flying
		
		if flying then
			local bv = Instance.new("BodyVelocity")
			bv.Name = "Fly"
			bv.MaxForce = Vector3.new(999999,999999,999999)
			bv.Parent = rootPart
			
			while flying do
				bv.Velocity = workspace.CurrentCamera.CFrame.LookVector * speed
				wait()
			end
			
			bv:Destroy()
		end
	end
end)

-- วิ่งเร็ว
humanoid.WalkSpeed = 30
