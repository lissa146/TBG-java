# TBG-java
<!DOCTYPE html>
<html>

<head>
    <title>Mini Adventure Game</title>
    <style>
        #gameImage {
            max-width: 100%;
            height: auto;
            margin: 20px 0;
        }
    </style>
</head>

<body>

    <!-- HTML: Game content -->

    <h2 id="roomTitle">Room Title</h2>
    <img id="gameImage" src="" alt="Room Image">
    <p id="roomDescription">Room Description</p>

    <!-- User input -->
    <input type="text" id="userInput" placeholder="Type your command">
    <button onclick="processCommand()">Go</button>

    <!-- JavaScript: Game logic -->

    <script>
        // Game rooms
        var rooms = {
            'start': {
                'title': 'The Mysterious Dungeon',
                'description': 'You are in a dark, cold dungeon. There are doors to the north and east.',
                'image': 'start-room.jpg',
                'directions': {
                    'north': 'library',
                    'east': 'laboratory',
                    'south': 'bedrooms'
                }
            },
            'library': {
                'title': 'The Ancient Library',
                'description': 'You find yourself surrounded by dusty books. There\'s a door to the south.',
                'image': 'library.jpg',
                'directions': {
                    'south': 'start'
                }
            },
            'laboratory': {
                'title': 'The Alchemist\'s Laboratory',
                'description': 'Strange potions bubble on the stove. There\'s a door to the west.',
                'image': 'laboratory.jpg',
                'directions': {
                    'west': 'start',
                    'south': 'jail'

                }
            },
            'jail': {
                'title': 'the dirty jail',
                'description': 'the jail have skeletons i guess they were here for a long time.',
                'image': 'skeletons.jpg',
                'directions': {
                    'north': 'laboratory',
                    'west': 'bedrooms'
                }
            },
            'bedrooms': {
                'title': 'the sleeping areaing',
                'description': 'these monsters are sleeping i need to be quiet,',
                'image': 'monsters.jpg',
                'directions': {
                    'north': 'start',
                    'east': 'jail',
                    'south': 'diningroom'
                }

            },
            'diningroom': {
                'title': 'this is were they eat',
                'description': 'its messly in here it seems like they just ate a bunch of food',
                'image': 'diningroom.jpg',
                'directions': {
                    'north': 'bedroom',
                    'south': 'kitchen'
                }
            },
            'kitchen': {
                'title': 'the where they cook food',
                'description': 'this is were the monsters cook there food surpininly clean.',
                'image': 'kitchen.jpg',
                'directions': {
                    'north': 'diningroom',
                    'south': 'outside'
                }
            },
            'outside': {
                'title': 'the forest',
                'description': 'you are outside the dongen.',
                'image': 'outside.jpg',
                'directions': {
                    'north': 'kitchen'
                }
            }

        };

        var currentRoom = 'start'; // Starting room
        updateRoom();

        function processCommand() {
            var command = document.getElementById('userInput').value.toLowerCase();
            var directions = rooms[currentRoom].directions;

            if (directions[command]) {
                currentRoom = directions[command];
                updateRoom();
            } else {
                alert('You cannot go that way.');
            }

            document.getElementById('userInput').value = ''; // Clear input field
        }

        function updateRoom() {
            var room = rooms[currentRoom];
            document.getElementById('roomTitle').innerText = room.title;
            document.getElementById('roomDescription').innerText = room.description;
            document.getElementById('gameImage').src = room.image;
        }
    </script>

</body>

</html>
