<script lang="ts">
	import { Presentation, Slide, Notes } from '@components'
	import Layout from './layout.svelte'
</script>

<Presentation>	
	<script>
		// information about this presentation 
		const author = "Daybreak"; 
		const title = "Milestone 4";
		const subtitle = "Evaluation";
		const department = "Department of Informatics"; 
		const university = "Technical University of Munich"; 
		var currentChapterName="";
		var currentChapterNumber=0;
		var chapterNames=[];
		var toc = false;  // whether toc is to be generated
		// data structure: [chapter number, chapter name, slideID]
		var presentationData = []; 
		function newChapter(chapterName){
			currentChapterName=chapterName; 
			currentChapterNumber++;
			chapterNames.push(chapterName);
		}
		// called when new slide is created
		var page=0; 
		function newPage(){
			page++; //note that page n has index n-1
			presentationData.push({chapternr: currentChapterNumber, chapter:currentChapterName,pagenr:page});
		}
	</script>

	<!-- title page -->
	<Slide>
		<Layout>
			<div class="m-16 flex h-[25vh] w-[90vw] bg-[var(--themecolor)] text-white items-center justify-center gap-[100px]">
				<div>
					<div class="text-[6vh]">
						<span id="mytitle"> </span>
					</div>
					<br>
					<div class="text-[4vh]">
						<span id="mysubtitle"> </span>
					</div>
				</div>
			</div>
			<br>
			<div> 
				<span id="myname"></span>
			</div>
			<br>
			<div class="text-[3vh]"> 
				<span id="myuni"></span>
			</div>
			<div class="text-[3.5vh]"> 
				<br>
				<span id="mydate"></span>
			</div>
			<br>
			<div class="flex items-center justify-center">
				<img class="h-[10vh] align-middle" src="/idp-slides/dAYBrEAk logo.png" alt="logo">
			</div>
			<!-- fill in the data for this presentation  -->
			<script> 
				document.getElementById("mytitle").innerHTML=title;
				document.getElementById("mysubtitle").innerHTML=subtitle;
				document.getElementById("myname").innerHTML="Team "+author;
				document.getElementById("myuni").innerHTML=university;
				let today = new Date(); 
				document.getElementById("mydate").innerHTML=today.toISOString().split('T')[0]; 
			</script>
		</Layout>
	</Slide>
	<!-- TOC -->
	<Slide>
		<script>
			toc=true; // decides whether to generate table of content page
		</script>
		<Layout>
			<toc class="flex h-full items-center justify-center gap-[100px]">
				<chpicons> </chpicons>
				<chpnames class="text-left"> </chpnames>
			</toc>
		</Layout>
	</Slide>

	<script>newChapter("Previously in Daybreak");</script>
	<Slide>
		<Layout>
			<div class="titlebar">
				Reminder: our HMWQ 
			</div>
			<div class="pt-[10vh] px-[20vh] text-left">
				<div>How can we guide </div>	<br>
				<div><span class="text-green-800">non-expert </span> employees in case of </div><br>
				<div><span class="text-green-800">small problems</span>, such as robot reconfiguration and restart, </div><br>
				<div>in order to make them </div><br>
				<div><span class="text-green-800">less dependent</span> on the manufacturer or the expert?</div><br>
			</div>
		</Layout>
	</Slide>

	<Slide><Layout> 
		<div class="titlebar">
			Reminder: our HMWQ 
		</div>
		<div class="pt-[5vh]">
			<ul class="a">
				<li> Our problem: </li>
				<ul class="b">
					<li>(From interview) robot is stuck at wall, yet interviewee has to come as he is the only one that is willing to fix it.</li>
					<li>Average workers are not comfortable with small fixes.</li>
				</ul>
			</ul>
			<ul class="a">
				<li>Our users: Non-expert workers that interact with robots on a regular basis. </li>
			</ul>
			<ul class="a"> 
				<li>Our solution: </li>
				<ul class="b">
					<li>Diagnostic AI to ease problem and finding</li>
					<li>Remote assistance in case expert help is needed</li>
					<li>Gamification to make the robot more approachable</li>
				</ul>
			</ul>
		</div>
	</Layout></Slide>

	<script>newChapter("Iteration 1: Exploration");</script>
	<Slide>
		<Layout>
			<div class="titlebar">
				Takeaways from the evaluation of iteration 3 (prototype)
			</div>
			<div class="pt-[5vh] ">
				<ul class="a">
					<li>Feedbacks:</li>
					<ul class="b">
						<li>Gadgets like rasperry pi is intimidating. </li>
						<li>Other languages than English is desirable. </li>
						<li>UI could be more approachable.</li>
					</ul>
				</ul>
				<ul class="a">
					<li>Solution: readjust the prototype. </li>
				</ul>
			</div>
	</Layout></Slide>

	<script> newChapter("Iteration 2: Ideation"); </script>
	<Slide><Layout>
			<div class="titlebar">
				How to implement the changes
			</div>
		<div class="pt-[10vh]">
			<ul class="a">
				<li>Convert physical parts of prototype into virtual version. </li><br>
				<li>Online version, accessed everywhere: click 
					<a href="https://www.figma.com/proto/Tim91iIaLVHV2bRLRc7HO7/Berkay-Geyik's-team-library-(Copy)?type=design&node-id=2316-739&t=egjcOFyxlofHQm0t-1&scaling=contain&page-id=0%3A1&starting-point-node-id=3538%3A636" target="_blank"
						class="text-green-600 u">
						here</a>
					to open. 
				</li>
				<br>
				<li>Implemente multi-lingual interface. </li><br>
			</ul>
		</div>
	</Layout></Slide>
	
	<script>newChapter("Iteration 3: Prototyping");</script>
	<Slide><Layout>
		<div class="titlebar">
			Implementing the changes: Physical parts into virtual version
		</div>
			<img src="/idp-slides/virtual.png" alt="virtual" class="h-[70vh] mx-auto my-[3vh]">
	</Layout></Slide>

	<Slide><Layout>
		<div class="titlebar">
			Implementing the changes: Online version, accessed everywhere
		</div>
		<br>
		<ul class="a">
			<li>Online version, accessed everywhere: click 
				<a href="https://www.figma.com/proto/3opdful8Js140VPQ0GglFL/Berkay-Geyik's-team-library?type=design&node-id=2316-739&t=lLxNp0QvCXC0mPqP-1&scaling=contain&page-id=0%3A1&starting-point-node-id=2316%3A739&mode=design" target="_blank"
					class="text-green-600 u">
					here</a>
				to open. 
			</li>
		</ul>
		<figure class="w-[45vw] float-left ml-[5vh] mt-[5vh]">
			<img src="/idp-slides/virtual.png" alt="virtual" class="h-[30vh] mx-auto my-[3vh]">
			<figcaption>Screen on the robot</figcaption>
		</figure>
		<figure class="w-[45vw] float-right mr-[5vh] mt-[5vh]">
			<div class="flex mx-[10vh]">
				<img src="/idp-slides/english.png" alt="app" class="h-[30vh] my-[3vh] mx-[5vh] ">
				<img src="/idp-slides/figma-tama.png" alt="app" class="h-[30vh] my-[3vh] mx-[5vh]">
			</div>
		<figcaption>App on your phone</figcaption>
		</figure>
	</Layout></Slide>

	<Slide><Layout>
		<div class="titlebar">
			Implementing the changes: Multi-lingual interface
		</div>
		<div class="pt-[1vh]">
			<ul class="a">
				<li>Implemente multi-lingual interface. </li><br>
			</ul>
			<figure class="mx-auto w-[45vw]">
				<img src="/idp-slides/french.png" alt="french" class="h-[50vh] mx-auto my-[1vh]">
				<figcaption>French menu</figcaption>
			</figure>
		</div>
	</Layout></Slide>

	<Slide>
		<Layout>
			<Notes> 
			- What evaluation methods would help the most for your prototype?
			- What aspects of the prototype need special evaluation? Is there a focus?
			- How can we include the feedback from users in the existing prototypes?
			</Notes>
			<div class="titlebar">
				The new and improved prototype: Fix-a-bot 
			</div>
			<br>
			<ul class="a">
				<li>Name: <img style="display:inline" src="/idp-slides/product-logo.png" alt="logo">
				</li> <br>
				<li style="font-style:italic"> Slogan: Every bot is fixable with Fix-a-bot. </li>
			</ul>
			<ul class="a">
				<li>Features:  </li>
				<ul class="b">
					<li>Diagnostic AI that comes with on-robot diagnostic and maintenance screen</li>
					<li>Remote assistance with AR support on your phone </li>
					<li>Virtual robot pet for increased intimacy </li>
				</ul>
			</ul>



		</Layout>
	</Slide>
	<Slide>
		<Layout>
			<div class="titlebar">
				Next step: evaluation
			</div>
			<br>
			<ul class="a">
				<li> Specific user group: interviews to get qualitative results. </li>
			</ul>
			<ul class="a">
				<li>Possible improvements to bring to the prototype. </li>
			</ul>
		</Layout>
	</Slide>

	<script>newChapter("Iteration 4: Evaluation");</script>
	<Slide>
		<Layout>
			<Notes> 
				- Who do you to evaluate your solution?
				- How can you reach them?
				- Is your idea a realistic solution to your problem?
				- Does your solution answer the HMW-Question?
				- Is your solution really new?
				- Is your solution really true?
				- Does your solution really matter?
			</Notes>
			<div class="titlebar">
				Who can evaluate?
			</div>
			<br>
			<ul class="a">
				<li>5 interviewees: suitable user known from (previous) work; people recommended by our previous interviewees of iteration 1. </li>
			</ul>
		</Layout>
	</Slide>
		
	<Slide>
		<Layout>
			<div class="titlebar">
				Evaluation results
			</div>
			<Notes>
				Feedbacks on the prototype: 
This person works with non-expert employees, trying to help them gain confidence with the robot. He is not our user group, but he sees every day how non-expert employees approach problems (we don't have to say that, it is just for you guys).
General feedback: There is a lack of images everywhere. If your user group is non-expert employees, you will need to treat them like children. So, put more signs and images almost everywhere.
Feedback 1: You should start showing your prototype with the QR that enables the user to download the app and let the user open the app and experience this part before showing what to do in case of problems. For me, your prototype was a good idea, but I think you should add the possibility of getting a notification if a problem is found so that employees can receive the message from any part of the company.
Feedback 2: The screen on the robot needs always an emergency button that you can click in case of an emergency.
Feedback 3: Add more 'Help me' notifications or signs on the app and on the screen! When the robot stops, add an animation on the main screen of the robot asking for help with a comic bubble. If the robot is equipped with warning lights, make a red lamp flash. Your prototype gave me the idea that the problem was a normal thing to encounter.
Feedback 4: Small error that we've encountered:
In the section where errors are displayed, it is better to always add images with a detailed description of the solution. The most common errors may include:
EMERGENCY BUTTON ACTIVATION (https://plc-trade.com/pub/20621/3su1100-1hb20-1cg0.jpg)
LOST LOCATION, use manually programmed RELOCATION POINTS on the virtual map and physically mark them on the floor with stickers. Then, physically bring the robot to that point and click on the touchscreen monitor on the name of the point where it is located. Usually when a company sells you a robot you have to mapp the area. They suggest you to put some relocations points on particular locations, so that if a robot get lost you can bring it to one of these points and restart it from there 
In the "Maintenance" section: Add photos of the general external cleaning of the casing, wheels, and sensors using specific sprays and microfiber cloths to avoid scratching them (example of sensors https://www.sick.com/it/it/prodotti-e-soluzioni/prodotti/sensori-lidar-e-radar/sensori-lidar/c/g575802)
Of course, the robot we are talking about is an AGV, so if you want to know more about the regulations it must comply with, you can refer to this document that briefly summarizes the most important things. Perhaps you are only interested in the chapters "Essential Safety Requirements" and "Maintenance Procedures" https://thesis.unipd.it/retrieve/787d3f0b-0c3d-4e60-9258-c0ca3fab4b92/Tonin_Alessandro.pdf
For example, this is the brand we use https://www.youtube.com/watch?v=jRTc695CANU&ab_channel=OmronAutomation-Americas
			</Notes>

			<ul class="a">
				- Is your idea a realistic solution to your problem?
			</ul>
			<ul class="a">
				- Does your solution answer the HMW-Question?
			</ul>
			<ul class="a">
				- Is your solution really new?
			</ul>
			<ul class="a">
				- Is your solution really true?
			</ul>
			<ul class="a">
				- Does your solution really matter?
			</ul>

		</Layout>
	</Slide>
	
	<Slide><Layout>
			<div class="titlebar">
				Possible improvements
			</div>
			<br>
			<ul class="a">
				<li> Improvement 1. </li>
				<li> Improvement 2. </li>
				<li> Improvement 3. </li>
				<li> Improvement 4. </li>
			</ul>
	</Layout></Slide>

	<Slide><Layout>
		<br>
		<img class="h-[60vh] mx-auto " src="https://media1.tenor.com/m/ktsa9WrPiKgAAAAC/friends-chandler-funny.gif" alt="dance">
		<br><div> Thank you! </div>
	</Layout></Slide>

	<!-- to mimic the latex template  -->
	<script>
		const totalSlides = document.getElementsByTagName('pagenumber').length;
		const totalChapters = chapterNames.length;
		var temp; 
		for (let i = 0; i < totalSlides; i++) {
			// one section, one slide
			document.getElementsByTagName('section')[i].setAttribute("id", "slide-"+(i+1));
			// add author name 
			document.getElementsByTagName('author')[i].innerHTML="<img src=\"/idp-slides/dAYBrEAk logo.png\" class=\"h-[4vh] pr-[0.5vh]\" > "+author ;
			// add title 
			document.getElementsByTagName('mytitle')[i].innerHTML="<a href=\"#slide-1\">"+title+": Evaluation"+"</a>";
			// show slide number with total slide number
			document.getElementsByTagName("pagenumber")[i].innerHTML = (i+1)+"/"+totalSlides;
		}
		for (let i = 0; i < totalSlides; i++) {
			for (let j = 0; j < totalChapters; j++) {
				// fill in chapter names
				temp = document.querySelectorAll("table.topbar")[i]; 
				temp.getElementsByTagName("tr")[0].innerHTML += "<th data-chpcol=\"chpcol\" style=\"font-weight:normal\">"+chapterNames[j]+"</th>";
				// fill in dots
				let slidesInChapter = presentationData.filter(item => item.chapter == chapterNames[j]);
				let begin = slidesInChapter[0].pagenr;
				let end = slidesInChapter[slidesInChapter.length-1].pagenr;
				let circles=toCircle(begin,end);
				temp.getElementsByTagName("tr")[1].innerHTML += "<td>"+ circles +"</td>";
			}
		}
		for (let i = 0; i < totalSlides; i++) {
			// first, find out if title page and toc exist 
			let chapter0 = presentationData.filter(item => item.chapternr == 0).length;
			if (i>=chapter0){
				// then set corresponding circle to white
				let circle = document.getElementsByTagName("circle-"+(i+1))[i]; 
				circle.style.background="white";
				circle.style.border="0px";
				// also the chapter names 
				let chapterNr = presentationData.filter(item => item.pagenr == i+1)[0].chapternr;
				temp = document.getElementsByTagName("th")[(i)*(totalChapters)+chapterNr-1];
				if (temp.hasAttribute("data-chpcol")){ 
					temp.style.color="white";
				}
			}
		}
		// circles: start, start+1, . . . , end are created
		function toCircle(begin,end){
			let circles = ""; 
			for (let i=begin; i<=end; i++){
				circles+="<a href=\"#slide-" +i+ "\"><circle-" +i+ " class=\"dot\"> </circle-" +i+ "> </a>" ;
			}
			return circles;
		}
		// to create table of contents
		if (toc) {
			for (i=1; i<=chapterNames.length;i++){
				document.getElementsByTagName('chpicons')[0].innerHTML += "<div class=\"chpicon\">"+i+"</div> <br>";
				document.getElementsByTagName('chpnames')[0].innerHTML += "<div>"+chapterNames[i-1]+"</div> <br>";
			}
		}
	</script>
	
	<style>
		.chpicon{
			color: white;
			width:180%;
			background: var(--themecolor);
		}
		.dot {
			height: 15px;
			width: 15px;
			background: rgba(0,0,0,0);
			border-radius: 50%;
			border: 1.5px solid var(--themecolorlight);
			display: inline-block;
		}
		.titlebar{
			background: rgb(242,242,242); 
			width: Z_FULL_FLUSH; 
			height: 9vh; 
			text-align: left;
			padding-left: 2vh; 
			padding-top: 2vh;
			font-size: 5vh;
		}

		ul.a {
			list-style-type: square;
			padding-top:4vh;
		}
		ul.b {
			list-style-type: circle;
			margin-left:5vh;
			margin-right:5vh;
			padding-top:2vh;
		}
		ul{
			text-align: left;
			margin-left:20vh;
			margin-right:5vh;
		}
		ul li {
			color: black;
		}
		figure {
			border: 1px #cccccc solid;
			padding: 4px;
			margin: auto;
		}
		figcaption {
			background-color: rgb(242,242,242);
			color: black;
			font-style: italic;
			padding: 2px;
			text-align: center;
		}
	</style>
</Presentation>