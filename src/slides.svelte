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
				<li>Online version, accessed everywhere. 
				</li>
				<br>
				<li>Implement multi-lingual interface. </li><br>
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
				<a href="https://www.figma.com/proto/Tim91iIaLVHV2bRLRc7HO7/Berkay-Geyik's-team-library-(Copy)?type=design&node-id=2316-739&t=egjcOFyxlofHQm0t-1&scaling=contain&page-id=0%3A1&starting-point-node-id=3538%3A636" target="_blank"
					class="text-green-600" style="text-decoration-line: underline;">
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
				<img src="/idp-slides/english.jpeg" alt="app" class="h-[30vh] my-[3vh] mx-[5vh] ">
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
				<li>Implement multi-lingual interface. </li><br>
			</ul>
			<figure class="w-[80vw]">
				<div class="flex mx-[2vh]">
					<img src="/idp-slides/virtual-fr.png" alt="french" class="h-[50vh] ml-[1vh]">
					<img src="/idp-slides/french.jpeg" alt="french" class="h-[50vh]  ml-[10vh]">
				</div>
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
				<li>Name: <img style="display:inline; height:5vh" src="/idp-slides/product-logo.png" alt="logo">
				</li> <br>
				<li > Slogan: <span style="font-style:italic">Every bot is fixable with Fix-a-bot.</span> </li>
			</ul>
			<ul class="a">
				<li>Features:  </li>
				<ul class="b">
					<li>Diagnostic AI that comes with on-robot diagnostic and maintenance screen</li>
					<li>Remote assistance with AR support on your phone </li>
					<li>Virtual robot pet for increased intimacy </li>
				</ul>
			<br>
			<li><a href="https://www.figma.com/proto/3opdful8Js140VPQ0GglFL/Berkay-Geyik's-team-library?type=design&node-id=2316-739&t=lLxNp0QvCXC0mPqP-1&scaling=contain&page-id=0%3A1&starting-point-node-id=2316%3A739" target="_blank" style="text-decoration-line:underline;" class="text-green-600">
				Short demo</a> 
				(<a href="https://www.figma.com/proto/IQ9UOg3RXt04rdCrNvxzZd/DiagnosticAI%2BARremoteassist-(english)?type=design&node-id=4-118&t=zUGlvzDJKeCfoxvi-0&scaling=scale-down&page-id=0%3A1&starting-point-node-id=4%3A118&show-proto-sidebar=1"target="_blank" style="text-decoration-line:underline;">
					link to QR</a>)
			</li>
			</ul>
	</Layout></Slide>

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
				<li>5 interviewees: 
				<ul class="b"> 
					<li>suitable user known from (previous) work experience</li> 
					<br>
					<li>people recommended by our previous interviewees of iteration 1</li>
				</ul>
			</ul>
		</Layout>
	</Slide>
	<Slide><Layout>
		<div class="titlebar">
			Evaluation results: positives
		</div>
		<ul class="a">
			<br>
			<li>In general, good idea. </li>
			<br>
			<li>Seems user friendly and easy to use.</li> <br>
			<li>Actually should help them reduce dependency on experts and solve problems quickly. </li><br>
			<li>Mobile app that runs diagnostic AI removely is helpful. </li>
		</ul>
	</Layout></Slide>
	<Slide>
		<Layout>
			<div class="titlebar">
				Evaluation results: improvements
			</div>
			<br>
			<ul class="a">
				<li>There could be more visual aides (e.g. images). </li>
				<ul class="b"> 
					<li>On the prototype in general</li>
					<li>On the description in case solution is found</li>
				</ul>
				<br>
				<li>The app should be easily accessible so users can familiarize with it regularly. </li>
				<br>
				<li>Implement notification system in case of problems. </li>
				<br>
			</ul>

		</Layout>
	</Slide>

	<Slide><Layout>
		<div class="titlebar">
			Evaluation results: improvements
		</div>
		<br>
		<ul class="a">
			<li>There should be a big emergency button on the on-bot screen. </li>
			<br>
			<li>More signs of robot asking for help, e.g. red blinking lights, animation on the screen...</li>
			<br>
			<li>Suggested some more commonly seen errors:</li>
				<ul class="b">
					<li>EMERGENCY BUTTON ACTIVATION</li>
					<!-- <img src="https://plc-trade.com/pub/20621/3su1100-1hb20-1cg0.jpg" alt="error" class="h-[20vh]"> -->
					<br>
					<li>LOST LOCATION</li>
				</ul>
		</ul>
	</Layout></Slide>
	<Slide><Layout>
		<div class="titlebar">
			Evaluation results
		</div>
		<ul class="a">
			<li>Icons in tamabotchi are confusing. </li> <br>
			<li>Holding the phone during remote assistance is tiring. </li> <br>
			<li>Cost of AR glasses might be high for clients. </li> <br>
			<li>Maintenance routine could instead be: </li>
			<ul class="b">
				<li>Regular maintenances that should be done</li>
				<li>When the expert was on site and what they did</li>
				<li>Errors and their solutions that do not need the diagnostic ai </li>
			</ul>
			<br>
			<li>Icon to select language could be bigger</li>
		</ul>
	</Layout></Slide>
	
	<Slide><Layout>
			<div class="titlebar">
				Possible improvements
			</div>
			<ul class="a">
				<li> Images, animation, blinking lights... </li>
				<br>
				<li> QR code to the app on the main page of on-bot screen. </li>
				<br>
				<li> Notification push in case of problems. </li>
				<br>
				<li> Emergency button on the main screen. </li>
				<br>
				<li> Modify icons on all parts of the prototype. </li>
				<br>
				<li>Modify maintainance contents. </li> <br>
				<li>...</li>
			</ul>
	</Layout></Slide>
	<Slide><Layout>
		<div class="titlebar">
			First attempts to implement some improvements (ongoing)
		</div>
		<br>
		<div class="flex mx-[2vh]">
			<figure class="w-[40vw] mt-[10vh]">
				<img src="/idp-slides/virtual-new.png" alt="french" class="h-[50vh]">
				<!-- <img src="/idp-slides/english-new.png" alt="french" class="h-[50vh]  ml-[10vh]"> -->
			</figure>
			<figure class="w-[40vw] mt-[10vh]">
				<div class="flex mx-[2vh]">
					<!-- <img src="/idp-slides/virtual-new.png" alt="french" class="h-[50vh] ml-[1vh]"> -->
					<img src="/idp-slides/english-new.png" alt="french" class="h-[50vh]  ml-[10vh]">
				</div>
			</figure>
		</div>
	</Layout></Slide>


	<script>newChapter("Summary");</script>
	<Slide><Layout>
		<div class="titlebar">
			Summary
		</div>
		<br>
		<ul class="a">
			<li>All in all, good idea, good interface. </li> <br>
			<li>Actually helps to solve the problem </li> <br>
			<li>But still a lot of potential for improvements</li> <br>
		</ul>

	</Layout></Slide>

	<Slide><Layout>
		<br>
		<img class="h-[60vh] mx-auto mt-[5vh]" src="https://media1.tenor.com/m/ktsa9WrPiKgAAAAC/friends-chandler-funny.gif" alt="dance">
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
