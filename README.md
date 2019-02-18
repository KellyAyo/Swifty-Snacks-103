<h2>Swifty Snacks 103: King of my castle?</h2>

Delegation, in iOS, is a communication pattern that enables 2 UIViews to communicate with each other.

To delegate, is to give a particular job to someone else so they can do it for you. In the context of iOS development, delegation is when a ‘Boss’ viewcontroller hands a job to a subservient ‘Intern’ viewcontroller — shout out to Sean Allan (YouTube iOS Dev Videos).

Let’s build a project, to demonstrate delegation in a simple fashion. We’re not about that storyboard life, so start by deleting Main.storyboard (see Swifty Snacks 101) and building a window through which to gaze into our sample project. The demo app will consist of two view controllers, specifically InternController & BossController. In AppDelegate assign InternController as our window’s rootViewController.

<img src="Swifty Snacks 103/image1.png">

As soon as our rootViewController (InternController) springs to life push an instance of BossController onto the stack.

<img src="Swifty Snacks 103/image2.png">

As you can see, BossController consists of a UIButton (dismissButton) positioned on top of a blue background.

We are now ready to code our simple implementation of the delegation design pattern: let’s empower our Boss to send commands to her intern.

Above class BossController: UIViewController { } define the protocol which our InternController must follow.

<img src="Swifty Snacks 103/image3.png">

Next define a variable ‘delegate’ as a weak reference to BossControllerDelegate, within the BossController class.

<img src="Swifty Snacks 103/image4.png">

Then reconfigure BossController’s dismissButton to a) dismiss the controller and b) make the Boss shout a command across to her Intern, via delegation.

<img src="Swifty Snacks 103/image5.png">

If we run our app now, the Bosses instruction will not be received by the Intern. To enable our Intern to receive commands, we need to make him conform to his Boss’s protocol.

<img src="Swifty Snacks 103/image6.png">

To finish we need to consider when it is most appropriate to formalise the relationship between the Boss and her Intern. The answer is to do so when pushing an instance of BossController onto the stack i.e. inside our pushBossController function.

<img src="Swifty Snacks 103/image7.png">

‘bc.delegate = self’ translates to BossController gives jobs to InternController (self) to execute. Now that the code is complete, pressing the dismiss button on BossController will remove it from the stack and change the backgroundColor of the InternController (below) to yellow.

“The world is changed by your example, not by your opinion.” — Paulo Coelho

