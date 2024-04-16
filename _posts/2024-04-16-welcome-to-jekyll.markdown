---
layout: post 
title: "Building a World with Code: Introducing My Language for Interactive Storytelling" 
date: 2024-04-16 20:11:02 +1000 
categories: programming worldbuilding
---


As a passionate developer and storyteller, I've always been fascinated by the idea of creating immersive worlds through code. That's why I've embarked on a journey to develop my own language specifically designed for world-building and interactive storytelling.

My language aims to provide a simple and intuitive way to define the elements of a story world, such as rooms, items, and their connections. By abstracting away the complexities of traditional programming languages, it allows creators to focus on the narrative aspects of their world.

At the core of my language are the following key components:

GameDefinition: This class serves as the foundation for building the game world. It allows you to create rooms, items, and establish connections between them.
{% highlight python %}
class GameDefinition:
  def __init__self):
    self.rooms = {}
    self.start_room = None

  def create_room(self, name, description):
      room = Room(name, description)
      self.rooms[name] = room
      if not self.start_room:
          self.start_room = room

  def create_item(self, room_name, item_name, item_description):
      item = Item(item_name, item_description)
      self.rooms[room_name].items.append(item)

  def connect_rooms(self, room1, room2, direction):
      self.rooms[room1].connections[direction] = self.rooms[room2]
      self.rooms[room2].connections[opposite_direction(direction)] = self.rooms[room1]
{% endhighlight %}

GameInterpreter: This class is responsible for interpreting the game definition and providing an interactive interface for players to explore the world.
{% highlight python %}
class GameInterpreter:
  def __init__(self):
    self.game = None
    self.current_room = None

  def load_game(self, game_definition):
      self.game = game_definition
      self.current_room = game_definition.start_room

  def play(self):
      print("Welcome to the Text Adventure Game!")
      while True:
          print("\nCurrent Room:", self.current_room.name)
          print("Description:", self.current_room.description)
          print("Items:", [item.name for item in self.current_room.items])
          print("Directions:", list(self.current_room.connections.keys()))
          command = input("> ").lower().split()
          if command[0] == "quit":
              print("Thanks for playing!")
              self.game.clear_game()
              break
          elif command[0] == "go":
              if len(command) > 1 and command[1] in self.current_room.connections:
                  self.current_room = self.current_room.connections[command[1]]
              else:
                  print("Invalid direction.")
          else:
              print("Invalid command.")
{% endhighlight %}

Item and Room: These classes represent the basic building blocks of the game world. Item defines the properties of objects that can be placed within rooms, while Room defines the characteristics of each location in the world.
{% highlight python %}
class Item:
  def __init__(self, name, description):
    self.name = name
    self.description = description

class Room:
  def __init__(self, name, description):
    self.name = name
    self.description = description
    self.items = []
    self.connections = {}
{% endhighlight %}

By combining these components, creators can easily define the structure and content of their game world. Here's an example of how a simple game can be defined and played using my language:

{% highlight python %}
from game_definition import GameDefinition
from game_interpreter import GameInterpreter

interpreter = GameInterpreter()

#Define game properly
game = GameDefinition()

#Create rooms
game.create_room("Living Room", "You are in the living room. It's cozy here.")
game.create_room("Kitchen", "You are in the kitchen. There's a delicious smell.")

#Create items
game.create_item("Living Room", "Couch", "A comfortable couch.")
game.create_item("Kitchen", "Stove", "A shiny stove.")

#Connect rooms
game.connect_rooms("Living Room", "Kitchen", "east")

#Play game
interpreter.load_game(game)
interpreter.play()
{% endhighlight %}

In this example, we define a simple game with two rooms (Living Room and Kitchen) and two items (Couch and Stove). The rooms are connected, allowing the player to navigate between them using cardinal directions.

By running the play() method of the GameInterpreter, players can interactively explore the world, move between rooms, and interact with the items they encounter.

My language is still in its early stages, but I have grand visions for its future. I plan to expand its capabilities to include more complex interactions, character dialogues, and dynamic events. The ultimate goal is to create a powerful yet accessible tool for world-building and interactive storytelling.

Stay tuned for updates on my language's development and future releases. I'm excited to see the incredible worlds and stories that creators will bring to life using this tool!