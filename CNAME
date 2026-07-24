// Main Application Class
class HardwarePrototypePresentationApp {
    constructor() {
        this.currentModule = null;
        this.currentSlide = 1;
        this.totalSlides = 30;
        this.isFullscreen = false;
        this.isPresenterMode = false;
        this.progress = this.loadProgress();
        this.settings = this.loadSettings();
        this.timer = {
            minutes: 0,
            seconds: 0,
            isRunning: false,
            interval: null
        };
        
        this.courseData = {
            title: "Build Your First Hardware Prototype with AI",
            subtitle: "A Complete Course for 10th Class Students",
            totalHours: 50,
            modules: [
                {
                    id: 1,
                    title: "Basic Electronics",
                    duration: "6 hours",
                    description: "Learn fundamentals of electricity, circuits, and basic components",
                    topics: ["Lab Safety", "Voltage & Current", "Ohm's Law", "Breadboarding", "LED Circuits"],
                    color: "#FF6B6B"
                },
                {
                    id: 2,
                    title: "Introduction to Microcontrollers", 
                    duration: "6 hours",
                    description: "Master Arduino programming and digital/analog I/O",
                    topics: ["Arduino Basics", "IDE Setup", "Digital I/O", "PWM", "Serial Communication"],
                    color: "#4ECDC4"
                },
                {
                    id: 3,
                    title: "Sensing the World",
                    duration: "6 hours", 
                    description: "Connect and use various sensors to read environmental data",
                    topics: ["Sensor Types", "Data Reading", "Serial Output", "Weather Station", "Integration"],
                    color: "#45B7D1"
                },
                {
                    id: 4,
                    title: "Simple AI with Hardware",
                    duration: "8 hours",
                    description: "Implement machine learning models on microcontrollers",
                    topics: ["AI Basics", "TinyML", "Data Collection", "Model Training", "Gesture Control"],
                    color: "#96CEB4"
                },
                {
                    id: 5,
                    title: "Designing with CAD",
                    duration: "5 hours",
                    description: "Create 3D models and enclosures for your projects",
                    topics: ["CAD Basics", "TinkerCAD", "3D Modeling", "Enclosure Design", "3D Printing"],
                    color: "#FFEAA7"
                },
                {
                    id: 6,
                    title: "Prototyping & Building", 
                    duration: "5 hours",
                    description: "Assemble complete prototypes with proper construction techniques",
                    topics: ["Fabrication", "Assembly", "Wiring", "Integration", "Testing"],
                    color: "#DDA0DD"
                },
                {
                    id: 7,
                    title: "Testing & Improve",
                    duration: "4 hours",
                    description: "Debug, test, and improve your hardware prototypes",
                    topics: ["Troubleshooting", "Multimeters", "Testing Plans", "Quality Control", "Iteration"],
                    color: "#FFB347"
                },
                {
                    id: 8,
                    title: "Final Project",
                    duration: "10 hours",
                    description: "Complete capstone project integrating all learned skills",
                    topics: ["Project Planning", "Implementation", "AI Integration", "Documentation", "Presentation"],
                    color: "#87CEEB"
                }
            ]
        };

        this.quizData = this.generateQuizData();
        this.init();
    }

    init() {
        this.renderModules();
        this.bindEvents();
        this.setupKeyboardNavigation();
        this.applySettings();
        this.updateOverallProgress();
    }

    // Module and Slide Data Generation
    generateSlideContent(moduleId) {
        const slideTemplates = {
            1: [ // Basic Electronics
                { title: "Basic Electronics", type: "title", content: "Understanding the fundamentals of electricity and circuits" },
                { title: "Learning Objectives", type: "list", content: ["Understand voltage, current, and resistance", "Build simple circuits on breadboards", "Use multimeters safely", "Create LED circuits", "Apply Ohm's Law"] },
                { title: "Lab Safety First", type: "safety", content: "Essential safety rules for electronics lab work" },
                { title: "What is Electricity?", type: "concept", content: "Flow of electrons through conductive materials" },
                { title: "Voltage Explained", type: "concept", content: "The 'pressure' that pushes electrons through a circuit" },
                { title: "Current Flow", type: "concept", content: "The rate of electron flow measured in Amperes" },
                { title: "Resistance", type: "concept", content: "Opposition to current flow measured in Ohms" },
                { title: "Ohm's Law", type: "formula", content: "V = I × R - The fundamental relationship" },
                { title: "Ohm's Law Practice", type: "activity", content: "Calculate voltage, current, and resistance values" },
                { title: "Circuit Components", type: "overview", content: "Resistors, LEDs, wires, and breadboards" },
                { title: "Reading Resistor Colors", type: "skill", content: "Decode resistance values from color bands" },
                { title: "Breadboard Anatomy", type: "hands-on", content: "Understanding power rails and tie points" },
                { title: "First Circuit Build", type: "activity", content: "Simple LED circuit with current-limiting resistor" },
                { title: "Series Circuits", type: "concept", content: "Components connected end-to-end in a line" },
                { title: "Parallel Circuits", type: "concept", content: "Components connected side-by-side" },
                { title: "Series vs Parallel", type: "comparison", content: "Voltage and current behavior differences" },
                { title: "Using a Multimeter", type: "tool", content: "Measuring voltage, current, and resistance" },
                { title: "Multimeter Practice", type: "activity", content: "Hands-on measurement exercises" },
                { title: "LED Characteristics", type: "component", content: "Forward voltage, current, and polarity" },
                { title: "Current Limiting", type: "concept", content: "Why we need resistors with LEDs" },
                { title: "Multiple LED Circuits", type: "hands-on", content: "Series and parallel LED arrangements" },
                { title: "Switch Integration", type: "hands-on", content: "Adding manual control to circuits" },
                { title: "Circuit Troubleshooting", type: "skill", content: "Finding and fixing common problems" },
                { title: "Power Sources", type: "concept", content: "Batteries, wall adapters, and USB power" },
                { title: "Circuit Documentation", type: "skill", content: "Drawing schematic diagrams" },
                { title: "Build Challenge", type: "project", content: "Design a traffic light circuit" },
                { title: "Project Presentation", type: "presentation", content: "Demonstrate your traffic light" },
                { title: "Knowledge Check", type: "quiz", content: "Test understanding of basic electronics" },
                { title: "What's Next?", type: "preview", content: "Introduction to programmable controllers" },
                { title: "Module 1 Complete", type: "completion", content: "You've mastered basic electronics!" }
            ],
            2: [ // Introduction to Microcontrollers
                { title: "Introduction to Microcontrollers", type: "title", content: "Arduino programming and digital control" },
                { title: "Learning Objectives", type: "list", content: ["Program Arduino microcontroller", "Control LEDs with code", "Read digital and analog inputs", "Use PWM for brightness control", "Debug with serial communication"] },
                { title: "What is a Microcontroller?", type: "concept", content: "A tiny computer that can control hardware" },
                { title: "Arduino Tour", type: "overview", content: "Pins, power, USB, and reset button" },
                { title: "Arduino IDE Setup", type: "hands-on", content: "Download, install, and configure" },
                { title: "First Sketch", type: "coding", content: "Blink LED - Hello World of hardware" },
                { title: "Code Structure", type: "coding", content: "setup() and loop() functions explained" },
                { title: "Digital Output", type: "coding", content: "digitalWrite() to control LEDs" },
                { title: "Digital Input", type: "coding", content: "digitalRead() to read button presses" },
                { title: "Pull-up Resistors", type: "concept", content: "Why buttons need pull-up resistors" },
                { title: "Button Control Activity", type: "activity", content: "Button controls LED on/off" },
                { title: "Analog Input", type: "coding", content: "analogRead() for sensor values" },
                { title: "Potentiometer Reading", type: "hands-on", content: "Read variable resistance values" },
                { title: "Analog Output (PWM)", type: "coding", content: "analogWrite() for brightness control" },
                { title: "Fade LED Activity", type: "activity", content: "Smoothly fade LED brightness" },
                { title: "For Loops", type: "coding", content: "Repeating actions with loops" },
                { title: "Variables and Data Types", type: "coding", content: "int, float, boolean, and char" },
                { title: "Conditional Statements", type: "coding", content: "if/else for decision making" },
                { title: "Serial Communication", type: "coding", content: "Print debug information to computer" },
                { title: "Serial Monitor Practice", type: "activity", content: "Debug sensor readings" },
                { title: "Functions", type: "coding", content: "Creating reusable code blocks" },
                { title: "Non-blocking Code", type: "advanced", content: "Using millis() instead of delay()" },
                { title: "Multiple LEDs", type: "project", content: "Control 8 LEDs in sequence" },
                { title: "Light Sensor Project", type: "project", content: "Automatic night light with LDR" },
                { title: "Temperature Logger", type: "project", content: "Read and log temperature data" },
                { title: "Code Challenge", type: "activity", content: "Create a simple alarm system" },
                { title: "Project Demonstration", type: "presentation", content: "Show your alarm system" },
                { title: "Programming Quiz", type: "quiz", content: "Test Arduino programming knowledge" },
                { title: "Debugging Skills", type: "skill", content: "Finding and fixing code errors" },
                { title: "Next Steps", type: "preview", content: "Connecting sensors to gather data" },
                { title: "Module 2 Complete", type: "completion", content: "You can now program Arduino!" }
            ],
            3: [ // Sensing the World
                { title: "Sensing the World", type: "title", content: "Connect sensors to gather environmental data" },
                { title: "Learning Objectives", type: "list", content: ["Connect various sensor types", "Read analog and digital sensors", "Process and display sensor data", "Build weather monitoring station", "Integrate multiple sensors"] },
                { title: "Types of Sensors", type: "overview", content: "Temperature, light, motion, distance, sound" },
                { title: "Analog vs Digital", type: "concept", content: "Continuous values vs on/off states" },
                { title: "Temperature Sensor", type: "hands-on", content: "TMP36 analog temperature reading" },
                { title: "Light Sensor (LDR)", type: "hands-on", content: "Photoresistor for light detection" },
                { title: "PIR Motion Sensor", type: "hands-on", content: "Detect human movement" },
                { title: "Ultrasonic Distance", type: "hands-on", content: "HC-SR04 for distance measurement" },
                { title: "Sound Sensor", type: "hands-on", content: "Microphone for sound level detection" },
                { title: "Sensor Calibration", type: "skill", content: "Converting raw values to real units" },
                { title: "Data Filtering", type: "advanced", content: "Smoothing noisy sensor readings" },
                { title: "Sensor Fusion", type: "concept", content: "Combining multiple sensors" },
                { title: "Display Options", type: "overview", content: "LEDs, LCD, OLED, serial monitor" },
                { title: "LCD Display Setup", type: "hands-on", content: "Connecting and controlling LCD" },
                { title: "Sensor Data Display", type: "activity", content: "Show temperature on LCD" },
                { title: "Data Logging", type: "skill", content: "Recording sensor data over time" },
                { title: "Threshold Alerts", type: "coding", content: "Trigger actions based on sensor values" },
                { title: "Multi-sensor Project", type: "project", content: "Environmental monitoring station" },
                { title: "Weather Station Build", type: "hands-on", content: "Temperature, humidity, light sensor" },
                { title: "Data Analysis", type: "activity", content: "Interpret collected sensor data" },
                { title: "Sensor Troubleshooting", type: "skill", content: "Fixing common sensor problems" },
                { title: "Wireless Sensors", type: "advanced", content: "Remote sensor networks" },
                { title: "IoT Integration", type: "concept", content: "Sending data to the internet" },
                { title: "Project Showcase", type: "presentation", content: "Demonstrate weather station" },
                { title: "Sensor Challenge", type: "activity", content: "Build motion-activated system" },
                { title: "Data Visualization", type: "skill", content: "Creating graphs and charts" },
                { title: "Sensor Quiz", type: "quiz", content: "Test sensor knowledge" },
                { title: "Real-world Applications", type: "discussion", content: "How sensors are used in industry" },
                { title: "Advanced Sensors", type: "preview", content: "Cameras, GPS, accelerometers" },
                { title: "Preparing for AI", type: "preview", content: "Sensors provide data for machine learning" },
                { title: "Module 3 Complete", type: "completion", content: "You can now sense the world!" }
            ],
            4: [ // Simple AI with Hardware
                { title: "Simple AI with Hardware", type: "title", content: "Implement machine learning on microcontrollers" },
                { title: "Learning Objectives", type: "list", content: ["Understand AI and machine learning basics", "Collect training data", "Train simple models", "Deploy AI to Arduino", "Build gesture-controlled projects"] },
                { title: "What is AI?", type: "concept", content: "Machines that can learn and make decisions" },
                { title: "Machine Learning Basics", type: "concept", content: "Teaching computers with examples" },
                { title: "TinyML Introduction", type: "concept", content: "AI on small, low-power devices" },
                { title: "Edge AI Benefits", type: "concept", content: "Fast, private, offline intelligence" },
                { title: "Types of Learning", type: "concept", content: "Supervised, unsupervised, reinforcement" },
                { title: "Data Collection", type: "hands-on", content: "Gathering sensor data for training" },
                { title: "Edge Impulse Setup", type: "hands-on", content: "Cloud platform for TinyML" },
                { title: "Accelerometer Data", type: "hands-on", content: "Capturing motion patterns" },
                { title: "Gesture Recognition", type: "project", content: "Teaching AI to recognize hand gestures" },
                { title: "Model Training", type: "hands-on", content: "Creating neural networks" },
                { title: "Model Testing", type: "activity", content: "Evaluating model accuracy" },
                { title: "Model Deployment", type: "hands-on", content: "Uploading AI to Arduino" },
                { title: "Voice Commands", type: "project", content: "Speech recognition on microcontroller" },
                { title: "Audio Processing", type: "advanced", content: "Converting sound to features" },
                { title: "Classification vs Regression", type: "concept", content: "Different types of AI problems" },
                { title: "Overfitting", type: "concept", content: "When models memorize instead of learning" },
                { title: "Model Optimization", type: "advanced", content: "Making models smaller and faster" },
                { title: "Real-time Inference", type: "hands-on", content: "Running AI predictions continuously" },
                { title: "Smart Home Controller", type: "project", content: "Gesture-controlled LED system" },
                { title: "AI Debugging", type: "skill", content: "Troubleshooting AI model issues" },
                { title: "Ethics in AI", type: "discussion", content: "Responsible AI development" },
                { title: "Bias in Data", type: "concept", content: "How bad data creates unfair AI" },
                { title: "AI Performance Metrics", type: "concept", content: "Accuracy, precision, recall" },
                { title: "Computer Vision Basics", type: "advanced", content: "Teaching AI to see" },
                { title: "AI Project Demo", type: "presentation", content: "Show your gesture controller" },
                { title: "AI Applications", type: "discussion", content: "How AI is changing the world" },
                { title: "Future of TinyML", type: "concept", content: "Emerging applications and possibilities" },
                { title: "AI Knowledge Check", type: "quiz", content: "Test AI understanding" },
                { title: "Advanced AI Topics", type: "preview", content: "Deep learning and neural networks" },
                { title: "Module 4 Complete", type: "completion", content: "You've built AI-powered hardware!" }
            ],
            5: [ // Designing with CAD
                { title: "Designing with CAD", type: "title", content: "Create 3D models and enclosures for projects" },
                { title: "Learning Objectives", type: "list", content: ["Use CAD software effectively", "Design custom enclosures", "Prepare files for 3D printing", "Iterate on designs", "Create professional documentation"] },
                { title: "What is CAD?", type: "concept", content: "Computer-Aided Design for creating 3D models" },
                { title: "Why Use CAD?", type: "concept", content: "Precision, visualization, and manufacturing" },
                { title: "TinkerCAD Introduction", type: "hands-on", content: "Browser-based CAD for beginners" },
                { title: "3D Thinking", type: "concept", content: "Visualizing objects in three dimensions" },
                { title: "Basic Shapes", type: "hands-on", content: "Cubes, cylinders, spheres as building blocks" },
                { title: "Shape Manipulation", type: "hands-on", content: "Move, rotate, scale, and duplicate" },
                { title: "Boolean Operations", type: "hands-on", content: "Combine shapes with union, difference, intersection" },
                { title: "Creating Holes", type: "hands-on", content: "Using negative shapes for holes" },
                { title: "Design Exercise 1", type: "activity", content: "Create a simple box with holes" },
                { title: "Measuring Tools", type: "hands-on", content: "Rulers and dimensions in CAD" },
                { title: "Precision Design", type: "skill", content: "Creating exact measurements" },
                { title: "Enclosure Design Principles", type: "concept", content: "Protection, access, and aesthetics" },
                { title: "Arduino Enclosure", type: "project", content: "Design case for Arduino project" },
                { title: "Component Clearance", type: "concept", content: "Leaving space for wires and connectors" },
                { title: "Mounting Solutions", type: "hands-on", content: "Standoffs, clips, and brackets" },
                { title: "Ventilation Design", type: "concept", content: "Airflow for heat dissipation" },
                { title: "User Interface Design", type: "concept", content: "Button and display placement" },
                { title: "Design Exercise 2", type: "activity", content: "Sensor housing with cable entry" },
                { title: "3D Printing Basics", type: "concept", content: "How 3D printers work" },
                { title: "Print Preparation", type: "hands-on", content: "Orientation, supports, and slicing" },
                { title: "Material Selection", type: "concept", content: "PLA, ABS, PETG properties" },
                { title: "Design for 3D Printing", type: "skill", content: "Overhangs, bridges, and tolerances" },
                { title: "Assembly Design", type: "concept", content: "Snap-fit connections and screws" },
                { title: "Prototyping Process", type: "concept", content: "Iterate, test, improve, repeat" },
                { title: "Professional CAD", type: "preview", content: "Fusion 360, SolidWorks overview" },
                { title: "Final Project Design", type: "project", content: "Complete enclosure for capstone project" },
                { title: "Design Review", type: "presentation", content: "Present and get feedback on design" },
                { title: "Manufacturing Alternatives", type: "concept", content: "Laser cutting, CNC machining" },
                { title: "Design Documentation", type: "skill", content: "Technical drawings and specifications" },
                { title: "Module 5 Complete", type: "completion", content: "You can now design like an engineer!" }
            ],
            6: [ // Prototyping & Building
                { title: "Prototyping & Building", type: "title", content: "Assemble complete prototypes professionally" },
                { title: "Learning Objectives", type: "list", content: ["Use rapid prototyping methods", "Assemble electronics properly", "Manage cables and connections", "Integrate hardware and software", "Build professional-quality prototypes"] },
                { title: "Prototyping Philosophy", type: "concept", content: "Fail fast, learn quickly, iterate often" },
                { title: "Prototyping Methods", type: "overview", content: "3D printing, laser cutting, cardboard, foam" },
                { title: "Tool Safety", type: "safety", content: "Safe use of cutting tools and hot equipment" },
                { title: "3D Printing Process", type: "hands-on", content: "From design to finished part" },
                { title: "Print Quality Issues", type: "troubleshooting", content: "Common problems and solutions" },
                { title: "Post-processing", type: "hands-on", content: "Cleaning, sanding, and finishing prints" },
                { title: "Assembly Planning", type: "skill", content: "Order of operations for building" },
                { title: "Fasteners and Hardware", type: "overview", content: "Screws, nuts, standoffs, and clips" },
                { title: "Soldering Basics", type: "hands-on", content: "Permanent electrical connections" },
                { title: "Soldering Practice", type: "activity", content: "Build a simple soldered circuit" },
                { title: "Wire Management", type: "skill", content: "Routing, securing, and labeling wires" },
                { title: "Connector Types", type: "overview", content: "Jumper wires, headers, terminals" },
                { title: "PCB Basics", type: "concept", content: "Printed circuit boards for permanent circuits" },
                { title: "Breadboard to PCB", type: "transition", content: "Moving from prototype to production" },
                { title: "Enclosure Assembly", type: "hands-on", content: "Installing electronics in custom cases" },
                { title: "Cable Entry Solutions", type: "skill", content: "Strain relief and weatherproofing" },
                { title: "User Interface Assembly", type: "hands-on", content: "Mounting buttons, displays, and indicators" },
                { title: "Testing During Assembly", type: "skill", content: "Incremental testing and validation" },
                { title: "Firmware Integration", type: "hands-on", content: "Loading final code onto hardware" },
                { title: "Calibration Procedures", type: "skill", content: "Adjusting sensors and outputs" },
                { title: "Documentation Creation", type: "skill", content: "Assembly instructions and user guides" },
                { title: "Quality Control", type: "concept", content: "Checking fit, finish, and function" },
                { title: "Prototype Evaluation", type: "activity", content: "Does it meet requirements?" },
                { title: "User Testing", type: "activity", content: "Get feedback from intended users" },
                { title: "Iteration Planning", type: "skill", content: "Prioritizing improvements" },
                { title: "Manufacturing Considerations", type: "concept", content: "Scaling from one to many" },
                { title: "Professional Finishing", type: "skill", content: "Labels, branding, and polish" },
                { title: "Portfolio Documentation", type: "skill", content: "Photos and videos of your work" },
                { title: "Build Showcase", type: "presentation", content: "Present your completed prototype" },
                { title: "Reflection and Planning", type: "activity", content: "What worked? What didn't?" },
                { title: "Module 6 Complete", type: "completion", content: "You can build professional prototypes!" }
            ],
            7: [ // Testing & Improve
                { title: "Testing & Improve", type: "title", content: "Debug, test, and improve hardware prototypes" },
                { title: "Learning Objectives", type: "list", content: ["Use systematic testing methods", "Debug hardware and software issues", "Measure prototype performance", "Apply quality control processes", "Iterate designs effectively"] },
                { title: "Testing Mindset", type: "concept", content: "Assume nothing works until proven otherwise" },
                { title: "Types of Testing", type: "overview", content: "Unit, integration, system, user acceptance" },
                { title: "Test Planning", type: "skill", content: "What to test and how to test it" },
                { title: "Multimeter Mastery", type: "hands-on", content: "Advanced measurement techniques" },
                { title: "Oscilloscope Basics", type: "hands-on", content: "Visualizing electrical signals" },
                { title: "Signal Analysis", type: "skill", content: "Reading waveforms and timing" },
                { title: "Hardware Debugging", type: "skill", content: "Finding electrical problems" },
                { title: "Software Debugging", type: "skill", content: "Using serial output and LED indicators" },
                { title: "Common Hardware Faults", type: "troubleshooting", content: "Loose connections, power issues, component failures" },
                { title: "Debugging Exercise", type: "activity", content: "Fix intentionally broken circuits" },
                { title: "Performance Testing", type: "concept", content: "Speed, accuracy, reliability metrics" },
                { title: "Environmental Testing", type: "concept", content: "Temperature, humidity, vibration effects" },
                { title: "User Interface Testing", type: "activity", content: "Is it easy to use?" },
                { title: "Load Testing", type: "concept", content: "How much can the system handle?" },
                { title: "Battery Life Testing", type: "hands-on", content: "Measuring power consumption" },
                { title: "Reliability Analysis", type: "concept", content: "Mean time between failures" },
                { title: "Quality Metrics", type: "concept", content: "Defining and measuring quality" },
                { title: "Test Documentation", type: "skill", content: "Recording test procedures and results" },
                { title: "Failure Analysis", type: "skill", content: "Understanding why things break" },
                { title: "Root Cause Analysis", type: "skill", content: "Finding the real source of problems" },
                { title: "Design for Testability", type: "concept", content: "Building in test points and diagnostics" },
                { title: "Automated Testing", type: "advanced", content: "Using computers to run tests" },
                { title: "Statistical Process Control", type: "concept", content: "Using data to control quality" },
                { title: "Continuous Improvement", type: "concept", content: "Always making things better" },
                { title: "Version Control", type: "concept", content: "Tracking changes and improvements" },
                { title: "Testing Challenge", type: "activity", content: "Find all bugs in mystery device" },
                { title: "Test Report Writing", type: "skill", content: "Communicating test results clearly" },
                { title: "Industry Standards", type: "concept", content: "Meeting safety and quality requirements" },
                { title: "Professional Testing", type: "overview", content: "How companies test products" },
                { title: "Testing Showcase", type: "presentation", content: "Present your testing methodology" },
                { title: "Module 7 Complete", type: "completion", content: "You can test and improve like a pro!" }
            ],
            8: [ // Final Project
                { title: "Final Project", type: "title", content: "Integrate all skills in capstone project" },
                { title: "Learning Objectives", type: "list", content: ["Plan complete hardware project", "Apply all learned skills", "Document work professionally", "Present finished prototype", "Reflect on learning journey"] },
                { title: "Your Journey So Far", type: "reflection", content: "Review skills from all 7 modules" },
                { title: "Capstone Project Goals", type: "concept", content: "Demonstrate mastery and creativity" },
                { title: "Project Requirements", type: "overview", content: "Minimum components and features needed" },
                { title: "Project Ideas", type: "brainstorm", content: "Smart home, health monitor, assistant device" },
                { title: "Problem Identification", type: "activity", content: "What real problem will you solve?" },
                { title: "Solution Design", type: "activity", content: "Sketch your approach" },
                { title: "Component Selection", type: "planning", content: "Choose sensors, outputs, and materials" },
                { title: "Timeline Creation", type: "planning", content: "Break project into manageable phases" },
                { title: "Risk Assessment", type: "planning", content: "What could go wrong?" },
                { title: "Project Proposal", type: "presentation", content: "Present plan for approval" },
                { title: "Prototype Development", type: "hands-on", content: "Build and test core functionality" },
                { title: "Milestone 1 Check", type: "checkpoint", content: "Basic functionality working" },
                { title: "Feature Integration", type: "hands-on", content: "Add advanced capabilities" },
                { title: "AI Model Training", type: "hands-on", content: "Collect data and train model" },
                { title: "Enclosure Fabrication", type: "hands-on", content: "3D print and assemble case" },
                { title: "Milestone 2 Check", type: "checkpoint", content: "All features implemented" },
                { title: "System Integration", type: "hands-on", content: "Combine all subsystems" },
                { title: "Comprehensive Testing", type: "hands-on", content: "Verify all requirements met" },
                { title: "User Interface Polish", type: "hands-on", content: "Make it user-friendly" },
                { title: "Documentation Creation", type: "writing", content: "Technical documentation and user guide" },
                { title: "Milestone 3 Check", type: "checkpoint", content: "Complete working prototype" },
                { title: "Presentation Preparation", type: "skill", content: "Prepare demo and slides" },
                { title: "Demo Day Practice", type: "activity", content: "Rehearse your presentation" },
                { title: "Final Presentations", type: "presentation", content: "Show off your amazing work!" },
                { title: "Peer Evaluation", type: "activity", content: "Learn from classmates' projects" },
                { title: "Project Reflection", type: "reflection", content: "What did you learn? What's next?" },
                { title: "Portfolio Completion", type: "documentation", content: "Compile all your work" },
                { title: "Career Pathways", type: "discussion", content: "Where these skills can take you" },
                { title: "Celebration", type: "celebration", content: "You did it! You're now a hardware hacker!" },
                { title: "Course Complete", type: "completion", content: "Congratulations on this amazing journey!" }
            ]
        };

        return slideTemplates[moduleId] || [];
    }

    generateQuizData() {
        return {
            1: [
                {
                    question: "What is Ohm's Law?",
                    options: ["V = I × R", "P = V × I", "I = V / R", "R = V × I"],
                    correct: 0,
                    explanation: "Ohm's Law states that Voltage equals Current times Resistance."
                },
                {
                    question: "What component limits current flow in an LED circuit?",
                    options: ["Capacitor", "Resistor", "Inductor", "Transistor"],
                    correct: 1,
                    explanation: "A resistor is used to limit current and prevent LED damage."
                }
            ],
            2: [
                {
                    question: "Which function runs only once when Arduino starts?",
                    options: ["loop()", "setup()", "main()", "start()"],
                    correct: 1,
                    explanation: "setup() runs once at the beginning of the program."
                },
                {
                    question: "What does PWM stand for?",
                    options: ["Power Width Modulation", "Pulse Width Modulation", "Program Width Mode", "Pulse Wave Mode"],
                    correct: 1,
                    explanation: "PWM stands for Pulse Width Modulation, used for analog-like output."
                }
            ],
            3: [
                {
                    question: "What type of sensor is a photoresistor?",
                    options: ["Digital", "Analog", "Both", "Neither"],
                    correct: 1,
                    explanation: "A photoresistor provides analog values that change with light intensity."
                }
            ],
            4: [
                {
                    question: "What does TinyML enable?",
                    options: ["Large AI models", "AI on microcontrollers", "Cloud computing", "Web development"],
                    correct: 1,
                    explanation: "TinyML enables machine learning on small, low-power devices."
                }
            ],
            5: [
                {
                    question: "What is a Boolean operation in CAD?",
                    options: ["Shape coloring", "Shape combining", "Shape measuring", "Shape copying"],
                    correct: 1,
                    explanation: "Boolean operations combine shapes using union, difference, or intersection."
                }
            ],
            6: [
                {
                    question: "Why is soldering preferred over breadboard connections in final prototypes?",
                    options: ["Cheaper", "Faster", "More reliable", "Easier to change"],
                    correct: 2,
                    explanation: "Soldered connections are permanent and more reliable than breadboard connections."
                }
            ],
            7: [
                {
                    question: "What tool visualizes electrical signals over time?",
                    options: ["Multimeter", "Oscilloscope", "Function generator", "Power supply"],
                    correct: 1,
                    explanation: "An oscilloscope displays how electrical signals change over time."
                }
            ],
            8: [
                {
                    question: "What is the main goal of a capstone project?",
                    options: ["Get good grades", "Demonstrate integrated learning", "Build something complex", "Use all components"],
                    correct: 1,
                    explanation: "A capstone project demonstrates integration and mastery of all course skills."
                }
            ]
        };
    }

    // Rendering Methods
    renderModules() {
        const modulesGrid = document.getElementById('modulesGrid');
        if (!modulesGrid) return;
        
        modulesGrid.innerHTML = '';

        this.courseData.modules.forEach(module => {
            const progress = this.progress.modules[module.id] || 0;
            const moduleCard = document.createElement('div');
            moduleCard.className = 'module-card';
            moduleCard.setAttribute('data-module', module.id);
            moduleCard.addEventListener('click', () => this.openModule(module.id));

            moduleCard.innerHTML = `
                <div class="module-header">
                    <div class="module-number">Module ${module.id}</div>
                    <h3 class="module-title">${module.title}</h3>
                    <div class="module-duration">⏱️ ${module.duration}</div>
                </div>
                <div class="module-body">
                    <p class="module-description">${module.description}</p>
                    <div class="module-topics">
                        ${module.topics.map(topic => `<span class="topic-tag">${topic}</span>`).join('')}
                    </div>
                    <div class="module-progress">
                        <div class="progress-bar">
                            <div class="progress-fill" style="width: ${Math.min(Math.max(progress, 0), 100)}%"></div>
                        </div>
                        <span class="progress-text">${Math.round(Math.min(Math.max(progress, 0), 100))}%</span>
                    </div>
                </div>
            `;

            modulesGrid.appendChild(moduleCard);
        });
    }

    openModule(moduleId) {
        this.currentModule = moduleId;
        this.currentSlide = 1;
        
        const courseOverview = document.getElementById('courseOverview');
        const presentationContainer = document.getElementById('presentationContainer');
        
        if (courseOverview) courseOverview.style.display = 'none';
        if (presentationContainer) presentationContainer.classList.remove('hidden');
        
        const moduleTitle = document.getElementById('currentModuleTitle');
        if (moduleTitle) {
            moduleTitle.textContent = `Module ${moduleId}: ${this.courseData.modules[moduleId - 1].title}`;
        }
        
        this.generateModuleSlides(moduleId);
        this.updateSlideCounter();
        this.updateProgress();
        this.updateNavigationButtons();
    }

    generateModuleSlides(moduleId) {
        const slidesContainer = document.getElementById('slidesContainer');
        if (!slidesContainer) return;
        
        slidesContainer.innerHTML = '';
        
        const slideData = this.generateSlideContent(moduleId);
        const moduleInfo = this.courseData.modules[moduleId - 1];

        slideData.forEach((slide, index) => {
            const slideNumber = index + 1;
            const slideElement = document.createElement('div');
            slideElement.className = `slide ${slideNumber === 1 ? 'active' : ''}`;
            slideElement.setAttribute('data-slide', slideNumber);

            let slideContent = this.generateSlideHTML(slide, slideNumber, moduleInfo);

            slideElement.innerHTML = `
                <div class="slide-content">${slideContent}</div>
                <div class="speaker-notes">
                    <h4>Speaker Notes:</h4>
                    <p>${this.generateSpeakerNotes(slide, slideNumber)}</p>
                    <p><strong>Duration:</strong> ${this.estimateDuration(slide)} minutes</p>
                </div>
            `;

            slidesContainer.appendChild(slideElement);
        });
    }

    generateSlideHTML(slide, slideNumber, moduleInfo) {
        switch (slide.type) {
            case 'title':
                return `
                    <div class="title-slide">
                        <h1>Module ${moduleInfo.id}: ${slide.title}</h1>
                        <h2>${slide.content}</h2>
                        <p class="course-info">${moduleInfo.duration} • ${slideNumber} slides • 🎯 ${moduleInfo.description}</p>
                        <div class="title-visual" style="color: ${moduleInfo.color}">
                            ${this.getModuleIcon(moduleInfo.id)}
                        </div>
                    </div>
                `;
            
            case 'list':
                return `
                    <h1>${slide.title}</h1>
                    <div class="content-list">
                        ${slide.content.map(item => `<div class="content-item">✅ ${item}</div>`).join('')}
                    </div>
                `;
            
            case 'concept':
                return `
                    <h1>${slide.title}</h1>
                    <div class="concept-main">
                        <h2>${slide.content}</h2>
                    </div>
                    <div class="concept-details">
                        ${this.getConceptDetails(slide.title)}
                    </div>
                `;
            
            case 'activity':
                return `
                    <h1>🎯 ${slide.title}</h1>
                    <div class="activity-box">
                        <h2>${slide.content}</h2>
                        <div class="activity-instructions">
                            ${this.getActivityInstructions(slide.title)}
                        </div>
                        <div class="activity-controls">
                            <button class="btn btn--primary" onclick="startTimer(${this.getActivityDuration(slide.title)})">
                                ⏱️ Start Timer
                            </button>
                        </div>
                    </div>
                `;
            
            case 'hands-on':
                return `
                    <h1>🔧 ${slide.title}</h1>
                    <div class="hands-on-content">
                        <h2>${slide.content}</h2>
                        <div class="hands-on-steps">
                            ${this.getHandsOnSteps(slide.title)}
                        </div>
                    </div>
                `;
            
            case 'quiz':
                return `
                    <h1>🧩 ${slide.title}</h1>
                    <div class="quiz-container">
                        <h2>Test your knowledge!</h2>
                        <div class="quiz-controls">
                            <button class="btn btn--primary" onclick="startQuiz(${moduleInfo.id})">
                                Start Knowledge Check
                            </button>
                        </div>
                    </div>
                `;
            
            case 'completion':
                return `
                    <div class="title-slide">
                        <h1>🎉 ${slide.title}</h1>
                        <h2>${slide.content}</h2>
                        <div class="completion-stats">
                            <div class="stat">
                                <span class="stat-number">${moduleInfo.id}</span>
                                <span class="stat-label">Module Complete</span>
                            </div>
                            <div class="stat">
                                <span class="stat-number">30</span>
                                <span class="stat-label">Slides Covered</span>
                            </div>
                        </div>
                        <div class="title-visual">🌟</div>
                    </div>
                `;
            
            default:
                return `
                    <h1>${slide.title}</h1>
                    <div class="slide-body">
                        <h2>${slide.content}</h2>
                        <div class="content-details">
                            ${this.getDefaultContent(slide.title, moduleInfo.id)}
                        </div>
                    </div>
                `;
        }
    }

    getModuleIcon(moduleId) {
        const icons = {
            1: '⚡🔧🔌',
            2: '🤖💻📟',
            3: '📡🌡️💡',
            4: '🧠🤖🎯',
            5: '🖥️📐🎨',
            6: '🔨🏗️⚙️',
            7: '🧪🔍📊',
            8: '🚀🎯🏆'
        };
        return icons[moduleId] || '🎯';
    }

    getConceptDetails(title) {
        // Generate relevant concept details based on title
        const conceptMap = {
            'What is Electricity?': '<p>Electricity is the flow of electrons through conductive materials. Understanding this flow is essential for building circuits.</p>',
            'Voltage Explained': '<p>Voltage is like water pressure in a pipe - it pushes electrons through the circuit. Measured in Volts (V).</p>',
            'Current Flow': '<p>Current is the rate of electron flow, like water flow rate. Measured in Amperes (A).</p>',
            'Resistance': '<p>Resistance opposes current flow, like friction in a pipe. Measured in Ohms (Ω).</p>'
        };
        return conceptMap[title] || '<p>Key concept in hardware prototyping.</p>';
    }

    getActivityInstructions(title) {
        const instructionMap = {
            'Ohm\'s Law Practice': '<ol><li>Calculate V when I=2A, R=100Ω</li><li>Calculate I when V=5V, R=250Ω</li><li>Calculate R when V=3.3V, I=0.02A</li></ol>',
            'First Circuit Build': '<ol><li>Insert LED into breadboard</li><li>Connect 220Ω resistor</li><li>Connect to 5V and Ground</li><li>Verify LED lights up</li></ol>',
            'Button Control Activity': '<ol><li>Connect button to digital pin</li><li>Enable pull-up resistor</li><li>Read button state</li><li>Control LED based on button</li></ol>'
        };
        return instructionMap[title] || '<p>Follow along with the hands-on activity.</p>';
    }

    getHandsOnSteps(title) {
        return '<ol><li>Gather required components</li><li>Follow wiring diagram</li><li>Test connections</li><li>Load and run code</li><li>Verify operation</li></ol>';
    }

    getActivityDuration(title) {
        const durations = {
            'Ohm\'s Law Practice': 10,
            'First Circuit Build': 15,
            'Button Control Activity': 20,
            'Fade LED Activity': 15,
            'Sensor Reading Activity': 25
        };
        return durations[title] || 15;
    }

    getDefaultContent(title, moduleId) {
        return '<p>Detailed content and examples will be provided during the lesson.</p>';
    }

    generateSpeakerNotes(slide, slideNumber) {
        const noteTemplates = {
            title: "Welcome students to the module. Build excitement about what they'll learn.",
            list: "Go through each objective. Ask students what they already know about these topics.",
            concept: "Use analogies and real-world examples. Check for understanding before moving on.",
            activity: "Circulate and help students. Encourage peer collaboration.",
            hands_on: "Demonstrate first, then let students try. Be ready to troubleshoot.",
            quiz: "This is formative assessment. Use results to identify knowledge gaps.",
            completion: "Celebrate achievements! Prepare students for the next module."
        };
        return noteTemplates[slide.type] || "Engage students and check for understanding.";
    }

    estimateDuration(slide) {
        const durations = {
            title: 3,
            list: 5,
            concept: 6,
            activity: 15,
            hands_on: 20,
            quiz: 10,
            completion: 3
        };
        return durations[slide.type] || 5;
    }

    // Navigation Methods
    nextSlide() {
        if (this.currentSlide < this.totalSlides) {
            this.goToSlide(this.currentSlide + 1);
        }
    }

    previousSlide() {
        if (this.currentSlide > 1) {
            this.goToSlide(this.currentSlide - 1);
        }
    }

    goToSlide(slideNumber) {
        const currentSlideElement = document.querySelector(`.slide[data-slide="${this.currentSlide}"]`);
        const nextSlideElement = document.querySelector(`.slide[data-slide="${slideNumber}"]`);
        
        if (currentSlideElement && nextSlideElement) {
            currentSlideElement.classList.remove('active');
            nextSlideElement.classList.add('active');
            
            this.currentSlide = slideNumber;
            this.updateSlideCounter();
            this.updateProgress();
            this.updateNavigationButtons();
            this.saveProgress();
        }
    }

    updateSlideCounter() {
        const slideCounter = document.getElementById('slideCounter');
        if (slideCounter) {
            slideCounter.textContent = `${this.currentSlide} / ${this.totalSlides}`;
        }
    }

    // FIXED: Progress bar update with proper containment
    updateProgress() {
        const progressPercent = Math.min(Math.max((this.currentSlide / this.totalSlides) * 100, 0), 100);
        const progressFill = document.getElementById('progressFill');
        
        if (progressFill) {
            // Ensure progress is properly constrained
            progressFill.style.width = `${progressPercent}%`;
        }
        
        // Update module progress with safety checks
        if (this.currentModule) {
            this.progress.modules[this.currentModule] = progressPercent;
        }
    }

    updateNavigationButtons() {
        const prevBtn = document.getElementById('prevBtn');
        const nextBtn = document.getElementById('nextBtn');
        
        if (prevBtn) prevBtn.disabled = this.currentSlide === 1;
        if (nextBtn) nextBtn.disabled = this.currentSlide === this.totalSlides;
    }

    // FIXED: Event Binding with proper event handling
    bindEvents() {
        // Navigation buttons - FIXED with proper event handling
        const prevBtn = document.getElementById('prevBtn');
        const nextBtn = document.getElementById('nextBtn');
        if (prevBtn) {
            prevBtn.addEventListener('click', (e) => {
                e.preventDefault();
                e.stopPropagation();
                this.previousSlide();
            });
        }
        if (nextBtn) {
            nextBtn.addEventListener('click', (e) => {
                e.preventDefault();
                e.stopPropagation();
                this.nextSlide();
            });
        }
        
        // Main navigation - FIXED
        const backToModulesBtn = document.getElementById('backToModulesBtn');
        const homeBtn = document.getElementById('homeBtn');
        if (backToModulesBtn) {
            backToModulesBtn.addEventListener('click', (e) => {
                e.preventDefault();
                e.stopPropagation();
                this.backToModules();
            });
        }
        if (homeBtn) {
            homeBtn.addEventListener('click', (e) => {
                e.preventDefault();
                e.stopPropagation();
                this.backToModules();
            });
        }
        
        // Modal buttons - FIXED
        const progressBtn = document.getElementById('progressBtn');
        const overviewBtn = document.getElementById('overviewBtn');
        const fullscreenBtn = document.getElementById('fullscreenBtn');
        const presenterBtn = document.getElementById('presenterBtn');
        const timerBtn = document.getElementById('timerBtn');
        const quizBtn = document.getElementById('quizBtn');
        const settingsBtn = document.getElementById('settingsBtn');
        
        if (progressBtn) {
            progressBtn.addEventListener('click', (e) => {
                e.preventDefault();
                e.stopPropagation();
                this.showProgressModal();
            });
        }
        if (overviewBtn) {
            overviewBtn.addEventListener('click', (e) => {
                e.preventDefault();
                e.stopPropagation();
                this.showOverviewModal();
            });
        }
        if (fullscreenBtn) {
            fullscreenBtn.addEventListener('click', (e) => {
                e.preventDefault();
                e.stopPropagation();
                this.toggleFullscreen();
            });
        }
        if (presenterBtn) {
            presenterBtn.addEventListener('click', (e) => {
                e.preventDefault();
                e.stopPropagation();
                this.togglePresenterMode();
            });
        }
        if (timerBtn) {
            timerBtn.addEventListener('click', (e) => {
                e.preventDefault();
                e.stopPropagation();
                this.showTimerModal();
            });
        }
        if (quizBtn) {
            quizBtn.addEventListener('click', (e) => {
                e.preventDefault();
                e.stopPropagation();
                this.showQuizModal();
            });
        }
        if (settingsBtn) {
            settingsBtn.addEventListener('click', (e) => {
                e.preventDefault();
                e.stopPropagation();
                this.showSettingsModal();
            });
        }
        
        // Modal close buttons
        document.querySelectorAll('.modal-close').forEach(btn => {
            btn.addEventListener('click', (e) => {
                e.preventDefault();
                e.stopPropagation();
                const modal = e.target.closest('.modal');
                if (modal) this.hideModal(modal.id);
            });
        });
        
        // Timer controls
        const startTimer = document.getElementById('startTimer');
        const pauseTimer = document.getElementById('pauseTimer');
        const resetTimer = document.getElementById('resetTimer');
        
        if (startTimer) {
            startTimer.addEventListener('click', (e) => {
                e.preventDefault();
                e.stopPropagation();
                this.startTimerControl();
            });
        }
        if (pauseTimer) {
            pauseTimer.addEventListener('click', (e) => {
                e.preventDefault();
                e.stopPropagation();
                this.pauseTimer();
            });
        }
        if (resetTimer) {
            resetTimer.addEventListener('click', (e) => {
                e.preventDefault();
                e.stopPropagation();
                this.resetTimer();
            });
        }
        
        // Quiz controls
        const submitQuiz = document.getElementById('submitQuiz');
        const nextQuestion = document.getElementById('nextQuestion');
        
        if (submitQuiz) {
            submitQuiz.addEventListener('click', (e) => {
                e.preventDefault();
                e.stopPropagation();
                this.submitQuiz();
            });
        }
        if (nextQuestion) {
            nextQuestion.addEventListener('click', (e) => {
                e.preventDefault();
                e.stopPropagation();
                this.nextQuestion();
            });
        }
        
        // Settings
        const saveSettings = document.getElementById('saveSettings');
        const resetSettings = document.getElementById('resetSettings');
        
        if (saveSettings) {
            saveSettings.addEventListener('click', (e) => {
                e.preventDefault();
                e.stopPropagation();
                this.saveSettings();
            });
        }
        if (resetSettings) {
            resetSettings.addEventListener('click', (e) => {
                e.preventDefault();
                e.stopPropagation();
                this.resetSettings();
            });
        }
        
        // FIXED: Click to advance slides - only for slide content, not buttons
        document.addEventListener('click', (e) => {
            // Only advance if clicking on slide content, not on any interactive elements
            if (e.target.closest('.slide-content') && 
                !e.target.closest('button') && 
                !e.target.closest('a') &&
                !e.target.closest('input') &&
                !e.target.closest('.modal') &&
                !e.target.closest('.presentation-nav') &&
                !e.target.closest('.nav-controls') &&
                !e.target.closest('.activity-controls') &&
                !e.target.closest('.quiz-controls') &&
                !e.target.matches('button') &&
                !e.target.matches('input')) {
                this.nextSlide();
            }
        });

        // Modal backdrop click to close
        document.querySelectorAll('.modal').forEach(modal => {
            modal.addEventListener('click', (e) => {
                if (e.target === modal) {
                    this.hideModal(modal.id);
                }
            });
        });
    }

    setupKeyboardNavigation() {
        document.addEventListener('keydown', (e) => {
            if (e.target.tagName === 'INPUT' || e.target.tagName === 'TEXTAREA') {
                return;
            }
            
            switch(e.key) {
                case 'ArrowRight':
                case ' ':
                    e.preventDefault();
                    this.nextSlide();
                    break;
                case 'ArrowLeft':
                    e.preventDefault();
                    this.previousSlide();
                    break;
                case 'f':
                case 'F11':
                    e.preventDefault();
                    this.toggleFullscreen();
                    break;
                case 'p':
                    e.preventDefault();
                    this.togglePresenterMode();
                    break;
                case 'o':
                    e.preventDefault();
                    this.showOverviewModal();
                    break;
                case 't':
                    e.preventDefault();
                    this.showTimerModal();
                    break;
                case 'Escape':
                    this.hideAllModals();
                    if (this.isFullscreen) {
                        this.toggleFullscreen();
                    }
                    break;
                case 'Home':
                    e.preventDefault();
                    this.goToSlide(1);
                    break;
                case 'End':
                    e.preventDefault();
                    this.goToSlide(this.totalSlides);
                    break;
            }
        });
    }

    // Modal Methods
    showProgressModal() {
        this.renderProgressModal();
        this.showModal('progressModal');
    }

    renderProgressModal() {
        const progressModules = document.getElementById('progressModules');
        if (!progressModules) return;
        
        progressModules.innerHTML = '';
        
        this.courseData.modules.forEach(module => {
            const progress = Math.min(Math.max(this.progress.modules[module.id] || 0, 0), 100);
            const moduleDiv = document.createElement('div');
            moduleDiv.className = 'progress-module';
            moduleDiv.innerHTML = `
                <div class="progress-module-info">
                    <div class="progress-module-title">Module ${module.id}: ${module.title}</div>
                    <div class="progress-module-stats">${Math.round(progress)}% complete • ${module.duration}</div>
                </div>
                <div class="progress-container">
                    <div class="progress-bar">
                        <div class="progress-fill" style="width: ${progress}%"></div>
                    </div>
                </div>
            `;
            progressModules.appendChild(moduleDiv);
        });
        
        this.updateOverallProgress();
    }

    updateOverallProgress() {
        const totalProgress = Object.values(this.progress.modules).reduce((sum, progress) => sum + (progress || 0), 0);
        const overallProgress = Math.min(Math.max(totalProgress / this.courseData.modules.length, 0), 100);
        
        const overallProgressEl = document.getElementById('overallProgress');
        const overallProgressText = document.getElementById('overallProgressText');
        
        if (overallProgressEl) overallProgressEl.style.width = `${overallProgress}%`;
        if (overallProgressText) overallProgressText.textContent = `${Math.round(overallProgress)}%`;
    }

    showOverviewModal() {
        this.renderSlideOverview();
        this.showModal('overviewModal');
    }

    renderSlideOverview() {
        const slideGrid = document.getElementById('slideGrid');
        if (!slideGrid || !this.currentModule) return;
        
        slideGrid.innerHTML = '';
        
        const slideData = this.generateSlideContent(this.currentModule);
        
        slideData.forEach((slide, index) => {
            const slideNumber = index + 1;
            const thumbnail = document.createElement('div');
            thumbnail.className = `slide-thumbnail ${slideNumber === this.currentSlide ? 'current' : ''}`;
            thumbnail.innerHTML = `
                <h4>${slide.title}</h4>
                <div class="slide-number">${slideNumber}</div>
            `;
            thumbnail.addEventListener('click', () => {
                this.goToSlide(slideNumber);
                this.hideModal('overviewModal');
            });
            
            slideGrid.appendChild(thumbnail);
        });
    }

    showTimerModal() {
        this.showModal('timerModal');
        this.updateTimerDisplay();
    }

    showQuizModal() {
        if (!this.currentModule) return;
        this.currentQuizIndex = 0;
        this.renderQuiz();
        this.showModal('quizModal');
    }

    renderQuiz() {
        const quizData = this.quizData[this.currentModule];
        if (!quizData || quizData.length === 0) {
            const quizQuestion = document.getElementById('quizQuestion');
            if (quizQuestion) {
                quizQuestion.innerHTML = '<p>No quiz available for this module.</p>';
            }
            return;
        }

        const currentQuiz = quizData[this.currentQuizIndex];
        const quizTitle = document.getElementById('quizTitle');
        const quizQuestion = document.getElementById('quizQuestion');
        
        if (quizTitle) quizTitle.textContent = `Module ${this.currentModule} Quiz`;
        if (quizQuestion) quizQuestion.textContent = currentQuiz.question;
        
        const optionsContainer = document.getElementById('quizOptions');
        if (optionsContainer) {
            optionsContainer.innerHTML = '';
            
            currentQuiz.options.forEach((option, index) => {
                const optionDiv = document.createElement('div');
                optionDiv.className = 'quiz-option';
                optionDiv.textContent = option;
                optionDiv.addEventListener('click', () => this.selectQuizOption(index));
                optionsContainer.appendChild(optionDiv);
            });
        }
        
        const quizFeedback = document.getElementById('quizFeedback');
        const submitQuiz = document.getElementById('submitQuiz');
        const nextQuestion = document.getElementById('nextQuestion');
        
        if (quizFeedback) quizFeedback.innerHTML = '';
        if (submitQuiz) submitQuiz.disabled = false;
        if (nextQuestion) nextQuestion.style.display = 'none';
    }

    selectQuizOption(index) {
        document.querySelectorAll('.quiz-option').forEach((option, i) => {
            option.classList.toggle('selected', i === index);
        });
        this.selectedQuizOption = index;
    }

    submitQuiz() {
        if (this.selectedQuizOption === undefined) return;
        
        const quizData = this.quizData[this.currentModule];
        const currentQuiz = quizData[this.currentQuizIndex];
        const isCorrect = this.selectedQuizOption === currentQuiz.correct;
        
        document.querySelectorAll('.quiz-option').forEach((option, i) => {
            if (i === currentQuiz.correct) {
                option.classList.add('correct');
            } else if (i === this.selectedQuizOption && !isCorrect) {
                option.classList.add('incorrect');
            }
        });
        
        const feedback = document.getElementById('quizFeedback');
        if (feedback) {
            feedback.className = `quiz-feedback ${isCorrect ? 'correct' : 'incorrect'}`;
            feedback.innerHTML = `
                <p>${isCorrect ? '✅ Correct!' : '❌ Incorrect'}</p>
                <p>${currentQuiz.explanation}</p>
            `;
        }
        
        const submitQuiz = document.getElementById('submitQuiz');
        const nextQuestion = document.getElementById('nextQuestion');
        
        if (submitQuiz) submitQuiz.disabled = true;
        if (nextQuestion && this.currentQuizIndex < quizData.length - 1) {
            nextQuestion.style.display = 'inline-block';
        }
    }

    nextQuestion() {
        this.currentQuizIndex++;
        this.selectedQuizOption = undefined;
        this.renderQuiz();
    }

    showSettingsModal() {
        this.showModal('settingsModal');
    }

    showModal(modalId) {
        const modal = document.getElementById(modalId);
        if (modal) {
            modal.classList.remove('hidden');
        }
    }

    hideModal(modalId) {
        const modal = document.getElementById(modalId);
        if (modal) {
            modal.classList.add('hidden');
        }
    }

    hideAllModals() {
        document.querySelectorAll('.modal').forEach(modal => {
            modal.classList.add('hidden');
        });
    }

    // Timer Methods
    startTimerControl() {
        if (!this.timer.isRunning) {
            this.timer.isRunning = true;
            this.timer.interval = setInterval(() => {
                if (this.timer.seconds > 0) {
                    this.timer.seconds--;
                } else if (this.timer.minutes > 0) {  
                    this.timer.minutes--;
                    this.timer.seconds = 59;
                } else {
                    this.timerComplete();
                    return;
                }
                this.updateTimerDisplay();
            }, 1000);
            
            const startBtn = document.getElementById('startTimer');
            if (startBtn) {
                startBtn.textContent = 'Running...';
                startBtn.disabled = true;
            }
        }
    }

    pauseTimer() {
        this.timer.isRunning = false;
        if (this.timer.interval) {
            clearInterval(this.timer.interval);
        }
        const startBtn = document.getElementById('startTimer');
        if (startBtn) {
            startBtn.textContent = 'Start';
            startBtn.disabled = false;
        }
    }

    resetTimer() {
        this.pauseTimer();
        this.timer.minutes = 0;
        this.timer.seconds = 0;
        this.updateTimerDisplay();
    }

    updateTimerDisplay() {
        const display = document.getElementById('timerDisplay');
        if (display) {
            const minutes = String(this.timer.minutes).padStart(2, '0');
            const seconds = String(this.timer.seconds).padStart(2, '0');
            display.textContent = `${minutes}:${seconds}`;
        }
    }

    timerComplete() {
        this.pauseTimer();
        alert('⏰ Time\'s up! Activity complete.');
        this.hideModal('timerModal');
    }

    // Utility Methods
    backToModules() {
        const presentationContainer = document.getElementById('presentationContainer');
        const courseOverview = document.getElementById('courseOverview');
        
        if (presentationContainer) presentationContainer.classList.add('hidden');
        if (courseOverview) courseOverview.style.display = 'block';
        
        this.currentModule = null;
        
        if (this.isFullscreen) {
            this.toggleFullscreen();
        }
        if (this.isPresenterMode) {
            this.togglePresenterMode();
        }
        
        this.renderModules(); // Refresh progress
    }

    toggleFullscreen() {
        const container = document.querySelector('.presentation-container');
        if (!container) return;
        
        if (!this.isFullscreen) {
            if (container.requestFullscreen) {
                container.requestFullscreen();
            } else if (container.webkitRequestFullscreen) {
                container.webkitRequestFullscreen();
            } else if (container.msRequestFullscreen) {
                container.msRequestFullscreen();
            }
            container.classList.add('fullscreen');
            this.isFullscreen = true;
            const fullscreenBtn = document.getElementById('fullscreenBtn');
            if (fullscreenBtn) fullscreenBtn.textContent = '🔍 Exit Fullscreen';
        } else {
            if (document.exitFullscreen) {
                document.exitFullscreen();
            } else if (document.webkitExitFullscreen) {
                document.webkitExitFullscreen();
            } else if (document.msExitFullscreen) {
                document.msExitFullscreen();
            }
            container.classList.remove('fullscreen');
            this.isFullscreen = false;
            const fullscreenBtn = document.getElementById('fullscreenBtn');
            if (fullscreenBtn) fullscreenBtn.textContent = '🔍 Fullscreen';
        }
    }

    togglePresenterMode() {
        const container = document.querySelector('.presentation-container');
        if (container) {
            container.classList.toggle('presenter-mode');
            this.isPresenterMode = !this.isPresenterMode;
            
            const btn = document.getElementById('presenterBtn');
            if (btn) {
                btn.textContent = this.isPresenterMode ? '👀 Hide Notes' : '👨‍🏫 Notes';
            }
        }
    }

    // Data Persistence - with error handling
    loadProgress() {
        try {
            const saved = localStorage.getItem('hardware-course-progress');
            if (saved) {
                return JSON.parse(saved);
            }
        } catch (error) {
            console.warn('Error loading progress:', error);
        }
        return {
            modules: {},
            lastModule: null,
            lastSlide: 1,
            completedQuizzes: []
        };
    }

    saveProgress() {
        try {
            this.progress.lastModule = this.currentModule;
            this.progress.lastSlide = this.currentSlide;
            localStorage.setItem('hardware-course-progress', JSON.stringify(this.progress));
        } catch (error) {
            console.warn('Error saving progress:', error);
        }
    }

    loadSettings() {
        try {
            const saved = localStorage.getItem('hardware-course-settings');
            if (saved) {
                return JSON.parse(saved);
            }
        } catch (error) {
            console.warn('Error loading settings:', error);
        }
        return {
            theme: 'dark',
            autoAdvance: false,
            transitionSpeed: 'normal'
        };
    }

    saveSettings() {
        try {
            const themeInput = document.querySelector('input[name="theme"]:checked');
            const autoAdvanceInput = document.getElementById('autoAdvance');
            const transitionSpeedInput = document.getElementById('transitionSpeed');
            
            const theme = themeInput ? themeInput.value : 'dark';
            const autoAdvance = autoAdvanceInput ? autoAdvanceInput.checked : false;
            const transitionSpeed = transitionSpeedInput ? transitionSpeedInput.value : 'normal';
            
            this.settings = { theme, autoAdvance, transitionSpeed };
            localStorage.setItem('hardware-course-settings', JSON.stringify(this.settings));
            this.applySettings();
            this.hideModal('settingsModal');
        } catch (error) {
            console.warn('Error saving settings:', error);
        }
    }

    resetSettings() {
        this.settings = {
            theme: 'dark',
            autoAdvance: false,
            transitionSpeed: 'normal'
        };
        try {
            localStorage.removeItem('hardware-course-settings');
        } catch (error) {
            console.warn('Error resetting settings:', error);
        }
        this.applySettings();
        
        // Reset form
        const darkTheme = document.querySelector('input[name="theme"][value="dark"]');
        const autoAdvance = document.getElementById('autoAdvance');
        const transitionSpeed = document.getElementById('transitionSpeed');
        
        if (darkTheme) darkTheme.checked = true;
        if (autoAdvance) autoAdvance.checked = false;
        if (transitionSpeed) transitionSpeed.value = 'normal';
    }

    applySettings() {
        // Apply theme
        if (this.settings.theme === 'light') {
            document.documentElement.setAttribute('data-color-scheme', 'light');
        } else {
            document.documentElement.removeAttribute('data-color-scheme');
        }
        
        // Apply transition speed
        const speeds = { fast: '0.2s', normal: '0.3s', slow: '0.5s' };
        document.documentElement.style.setProperty('--slide-transition-duration', 
            speeds[this.settings.transitionSpeed] || speeds.normal);
    }
}

// Global functions for inline event handlers
window.startTimer = function(minutes) {
    if (window.app) {
        window.app.timer.minutes = minutes;
        window.app.timer.seconds = 0;
        window.app.showTimerModal();
        window.app.startTimerControl();
    }
};

window.setTimer = function(minutes) {
    if (window.app) {
        window.app.timer.minutes = minutes;
        window.app.timer.seconds = 0;
        window.app.updateTimerDisplay();
    }
};

window.startQuiz = function(moduleId) {
    if (window.app) {
        window.app.showQuizModal();
    }
};

// Initialize the app when DOM is loaded
document.addEventListener('DOMContentLoaded', () => {
    window.app = new HardwarePrototypePresentationApp();
});

// Handle fullscreen change events
document.addEventListener('fullscreenchange', () => {
    const container = document.querySelector('.presentation-container');
    if (!document.fullscreenElement && window.app && container) {
        container.classList.remove('fullscreen');
        window.app.isFullscreen = false;
        const fullscreenBtn = document.getElementById('fullscreenBtn');
        if (fullscreenBtn) fullscreenBtn.textContent = '🔍 Fullscreen';
    }
});

// Handle window resize for responsive progress bars
window.addEventListener('resize', () => {
    if (window.app) {
        // Force progress bar recalculation on resize
        window.app.updateProgress();
        window.app.updateOverallProgress();
    }
});