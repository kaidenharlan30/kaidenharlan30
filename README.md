local hoopPosition = game.Workspace.Hoop.Position
local ballVelocity = game.Workspace.Ball.Velocity

-- Create a function to calculate the ball's trajectory
local function calculateTrajectory()
    -- Calculate the ball's initial velocity and direction
    local initialVelocity = ballVelocity
    local direction = (hoopPosition - ballPosition).unit

    -- Calculate the ball's trajectory using physics
    local trajectory = {}
    for i = 1, 100 do
        local position = ballPosition + initialVelocity * i
        table.insert(trajectory, position)
    end

    -- Return the trajectory
    return trajectory
end

-- Create an aimbot function
local function aimbot()
    -- Calculate the ball's trajectory
    local trajectory = calculateTrajectory()

    -- Find the closest point on the trajectory to the hoop
    local closestPoint = nil
    local closestDistance = math.huge
    for i, position in pairs(trajectory) do
        local distance = (position - hoopPosition).magnitude
        if distance < closestDistance then
            closestPoint = position
            closestDistance = distance
        end
    end

    -- Shoot the ball towards the closest point
    game.Workspace.Ball.Velocity = (closestPoint - ballPosition).unit * 100
end

-- Call the aimbot function repeatedly
while true do
    aimbot()
    wait(0.1)
endlocal player = game.Players.LocalPlayer
local ball = game.Workspace.Ball

while true do
wait(0.01)
local ballPosition = ball.Position
local myPosition = player.Character.HumanoidRootPart.Position
local distance = (ballPosition - myPosition).Magnitude
if distance < 5 then
ball.Velocity = Vector3.new(0, 0, 0)
ball.Position = myPosition
end
endlocal player = game.Players.LocalPlayer
local opposingTeam = game.Teams.OpposingTeam

while true do
wait(0.01)
for _, v in pairs(opposingTeam.Players) do
local guardPosition = v.Character.HumanoidRootPart.Position
local myPosition = player.Character.HumanoidRootPart.Position
if (guardPosition - myPosition).Magnitude < 5 then
player.Character.Humanoid:MoveTo(guardPosition)
wait(0.1)
player.Character.Humanoid:MoveTo(myPosition)
end
end\
endlocal logos = {}
