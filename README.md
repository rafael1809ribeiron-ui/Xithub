local Players = game:GetService("Players")
local RunService = game:GetService("RunService")
local Workspace = game:GetService("Workspace")

local BLOCK_SIZE = Vector3.new(6, 1, 6)
local BLOCK_COLOR = BrickColor.new("Bright blue")

local function createBlock(position)
    local block = Instance.new("Part")
    block.Size = BLOCK_SIZE
    block.Anchored = true
    block.TopSurface = Enum.SurfaceType.Smooth
    block.BottomSurface = Enum.SurfaceType.Smooth
    block.BrickColor = BLOCK_COLOR
    block.Position = position
    block.Parent = Workspace
end

Players.PlayerAdded:Connect(function(player)
    player.CharacterAdded:Connect(function(character)
        local hrp = character:WaitForChild("HumanoidRootPart")

        RunService.Heartbeat:Connect(function()
            if hrp and hrp.Parent then
                local belowPos = hrp.Position - Vector3.new(0, 4, 0)
                createBlock(Vector3.new(
                    math.floor(belowPos.X / 6) * 6,
                    math.floor(belowPos.Y),
                    math.floor(belowPos.Z / 6) * 6
                ))
            end
        end)
    end)
end)
# Xithub
