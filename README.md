# MarsRover.readme


#include<iostream>
#include<vector>

//  Interface using Command Pattern
class Command {
public:
    virtual void execute() const = 0;
};

// Command for Moving Forward
class MoveCommand : public Command {
public:
    void execute() const override {
        // Implementation for moving forward
        std::cout << "Moving forward\n";
    }
};

// Command for Turning Left
class LeftCommand : public Command {
public:
    void execute() const override {
        // Implementation for turning left
        std::cout << "Turning left\n";
    }
};

// Command for Turning Right
class RightCommand : public Command {
public:
    void execute() const override {
        // Implementation for turning right
        std::cout << "Turning right\n";
    }
};

// Receiver class for the Rover
class Rover {
public:
    void processCommands(const std::vector<Command*>& commands) {
        for (const auto& command : commands) {
            command->execute();
        }
    }
};

int main() {
    // Client code
    std::vector<Command*> commands;
    commands.push_back(new MoveCommand());
    commands.push_back(new MoveCommand());
    commands.push_back(new RightCommand());
    commands.push_back(new MoveCommand());
    commands.push_back(new LeftCommand());
    commands.push_back(new MoveCommand());

    Rover rover;
    rover.processCommands(commands);

    return 0;
}
