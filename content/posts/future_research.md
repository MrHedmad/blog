+++
title = "Future Open Research"
description = "My ideas about what research should look like in a FAIR and Open world"
date = "2024-10-25"
+++

In this piece, I hope to give an overall view of how I believe the future research "flow" should look like, given the ideas in the Open Science and FAIR  spaces, and how data stewards fit into the overall picture.

I'd like to place a disclaimer here. I am, in no shape or form, thinking that the ideas presented here would be easy to implement. However, I believe that delineating and keeping in mind the *golden standard* is essential while pursuing it.
These ideas also apply to *publicly funded* research. Privately funded research might not fit this schema, although I'd argue many aspects can be transversal.

![Research Flow](https://i.ibb.co/fG9KkGr/research-flow-dark.png)
> The proposed Open Research workflow. Please note that "Mimir protocols" refer to Structured protocols. 

First, we can define three large areas in the research process:
- The planning phase, before the project starts, when details about it are defined;
- The research process itself, when experiments are executed;
- The preservation and dissemination of the conducted research;

Data stewards and Open Science principles can help streamline and open up all three steps, creating a new, of fundamentally higher quality, research procedure.
I refer to this proposed structure as "Open Research" (OR).


> I often talk about Structured protocols. You can find more information on them [here](https://mrhedmad.github.io/mimir/prep/definitions.html) and [here](https://mrhedmad.github.io/mimir/prep/protocols.html). They are implemented well in the (paid) platform of [protocols.io](https://protocols.io).

> Bullet points starting with `$` are implementation questions that have to be effectively addressed before this research flow can be used in practice.

## Planning
The project planning phase is arguably the most important. 
OR begins as any research project does, by having an idea.
This idea, as is routinely done when applying for grants, is often fleshed out and plainly explained in a specific document.
OR extends this idea to every project, big or small, funded through grants or not.

When an individual or team is committed to the execution of the project, a *project space* is created with the ability to store project-level documentation and metadata. This platform is then used as a centralized place to effectively plan all the other steps.

- $ Which technology will be used to create the *project space*?
    - https://osf.io/ is a possibility, as well as Virtual Research Environments and more generic Electronic Lab Notebooks.

During this phase, many aspects of the overall project are defined:
- The rationale and assumptions that form the background of the project;
- The ultimate objective of the project, crucially with clear, *actionable* experimental questions;
- The methods that will be used to achieve the objective(s), in as much detail as this phase allows, including, if needed, the statistical methods that will be applied to the data;
    - A consultation with a statistician is crucial at this point.
- What the expected results are, if any.
    - While the practice of *expecting a result* is arguably negative - it may increase biases or trigger subconscious questionable research practices - it is in the nature of research to expect a particular outcome. It is therefore important to be aware of what the experimenter expects in order to mitigate potential biases.
- Where to ask for funding, if it is needed.

Depending on the scope of the project, this document, the *project plan*, may be large or small. It is important to underline that OR prescribes that *all* projects, of any size, are explicitly planned.

- $ How should this document be structured? Which guidelines (accounting for scope) should be created to support this process?
    - A potential way is to consult pre-registration platforms and re-use their guidelines.

If required, the funding proposal is created and included in the project space.

- $ How can we keep track of all the projects created by the university?
    - The CRIS informational system may be useful in this regard.

Crucially, after the project plan is created, a data steward is assigned to the project. The data steward has the role of guiding the researchers in all aspects of data management, from dealing with the fine points of FAIR data implementation to the education of researchers on Open Science concepts.

- $ Of course, the institution would need a group of data stewards to support this step.

The data steward begins guiding the group through the creation of a data management plan. The data types that are expected to be handled in the project are defined. Then, the data steward determines if FAIR Implementation Profiles (FIPs) created in the past can be used to deal with these data types.
If relevant FIPs exist, they can be reused or adapted to the current situation. Otherwise, new FIPs need to be created by the data steward, and deposited in the FIP archive for later reuse.

- $ What should be contained in a FIP? Where should the FIPs be archived? How can they be made both human- and machine-operable? How can we avoid FIP duplication? How can we effectively find relevant FIPs? 
  - In essence, we would need FAIR FIPs. 

Once data types, volumes, privacy concerns, corresponding FIPs and all other aspects regarding data management are determined, the data management plan can be redacted, and deposited as a deliverable in the project space.

- $ Which tools can be used to create the DMP? Which tools can help in the preliminary interview?
    - An example is the Data Stewardship Wizard.

After - and only after - the DMP is created, the true research process can begin.

## Active Research

> It is important to note that I am a researcher in the biological space, so my concept of *experiment* aligns with this field. I admit my ignorance of other research areas, and, while I try to present these ideas in a field-agnostic way, this discrepancy on conceptualization might cause some concepts presented here to not apply, at least directly, to all research fields.

The research process itself involves running experiments or, in general, gathering and processing knowledge.

It is crucial that each technically sound experiment or data collection (even if not ultimately useful to the goal of the project) is considered for long term preservation (see, for this, the discard problem).

Tools such as open notebooks and integrated research environments are particularly useful to open up research during this step.
However, due to the fast pace of the active research process, the complete transparency of this stage might not be an achievable goal.

A key aspect that enables future FAIR data creation is the usage of Structured protocols. They enable more or less automatic deposit of experimental data after the experiment is over. Of course, the guiding light during the experimental step is the specific FIP(s) previously defined in the DMP.

The Hot data produced during this step is temporarily stored in an agile repository.

- $ Where will this temporary storage be?
    - It strongly depends on the FIPs, since data of different kinds will need different hot storage solutions.

The experiments produce considerations, which drive more experiments, and so on. At any point, the DMP may be updated (with the same procedure followed when creating it) if and when new data types need to be used.

It is useful to apply a standardized structure for the hot data storage, to ease later processing.

The data steward acts as both support and supervisor, periodically checking if data quality is upheld, and if the processes as detailed in the FIPs are respected regarding data formats, content, etc...

OR should explicitly detail every experiment, with a mini-rationale statement and noting down the considerations made on the results.
This has two benefits. First, the researcher must consciously process why each experiment is run, and what information can be derived from it. Secondly, encapsulating data from each experiment individually makes later FAIRification both easier and in some cases possible. Structured protocols should help in this regard, if implemented and followed correctly.

> It might be possible to collate FIPs and Structured protocols into a single entity, which could be called FAIR-Enabled Structured Protocols.

All experiments, regardless of "positive" or "negative" outcome should be considered for preservation. Only identifiable violations of the structured protocols may warrant the outright deletion of the experimental data due to technical failure.
If the researcher still believes that the experiment failed (regardless of outcome), but the protocol breakage cannot be determined, the experiment can be retained but marked as potentially faulty.

A single experiment may be trying to answer more than one question, or might contain internal controls for quality assurance. Additionally, information regarding laboratory quality controls and known confounding factors need to be included in the metadata of the experiment.
This quality information must be recorded properly, and reflected in the final metadata.

The summarize, each experiment "block' has to carry the following information:
- The rationale of the experiment;
- The data itself, potentially already in the structure required by the FIP;
- The (annotated) run information of the Structured protocol used, as well as its version;
- The considerations made by the researcher on the resulting experiment.

To group this different information, an identifier can be used to mark all related files. FAIR Containers such as Research Object Crates (ROCrates) might be useful. 

## Preservation and dissemination
After the (main) experimental phase is completed, it is important to collate all experiments that where not discarded (again, regardless of outcome) and all considerations made on them into a large document which I'll call *interpretation*.
This document includes everything that was done during the experimental phase, and may or may not coincide with the laboratory notebook.

This document, when redacted, will be the starting point of both research articles and the way that data will be ultimately deposited in long-term repositories.

The researchers leave the data with the data stewards and may begin writing the manuscript for the publication process.

The data steward then begins working on archival and long-term preservation of the data, including the determination of access policies and other FAIR-enabling infrastructural choices.
According to the FIPs, data archival packages are created for the data that requires archival (the Discard problem can be re-evaluated here), and expiration dates (if needed) are placed on the data (see, for instance, Access-based lifetime determination). Data archival packages are collections of data, metadata, identifiers and generally all knowledge that is required for the data to be archived, including all of the information for its effective later reuse.

When archival packages are ready, they are deposited in the relevant repositories. It is useful to create a space to collate all identifiers of all the data created in a specific project, to preserve the identity of the project itself. A way to do this might be through Nanopublications (see later). While project identity is not necessarily useful for data reuse, it might be needed for quality evaluation and authorship rights in the later phases. 

- $ Where will they be deposited in? What shape do they have? What further processing has to be enabled by the structure of the archival packages?
    - All of this information has to be determined while creating the specific FIPs.

Nanopublications are minted from the archival packages, recording the salient metadata and forming a knowledge graph that may be used to access this data again later.

If software was used to analyse the data, or the project was the development of novel software, this has to be deposited statically into some archive.
- $ How can we achieve this? Is Docker enough?

The interpretation document can also be used (with the help of the original researcher) to derive basic assertions that can become nanopublications, enabling researchers to distill their findings and increasing their own and the community awareness on all of the outcomes of their research, were they expected or otherwise.
These nanopublications can then go and increase the global body of knowledge for further (automated) examination.

After all data is processed, checked for consistency and archived, and all relevant nanopublications are created and interlinked with the archived data, the project may be considered to be finished. All local data may be deleted, and project spaces closed.

This marks the end of the project. However, post-project data support may still be needed if third parties require access to data, for example for controlled data. This can be handled by either the data steward or the researchers themselves.

- $ Who has the legal responsibility over this data? Who is the data curator?
    - In theory, the day-to-day control of the data should be given to the institution, which has a longer lifespan than the individual author (while, of course, keeping authorship rights).

It is important to note that the publication procedure does not influence whether or not the resulting data and assertions are published. The data is deposited regardless of the attempt at a publication (for a "regular" project) or not (for, e.g. master theses), and whether or not the manuscript is accepted.
This ensures that no insight is lost, regardless of the (potentially fickle) publication procedures.

Green open access, when needed, has to be enforced by the institutions, arguably for ethical responsibilities for publicly-funded research.

## Self-evaluation
To keep this process able to comply with the needs of researchers, post-project meetings to define what worked and what did not, what can be done better, and other criticalities have to be performed. This self-audit has the be accessible for aggregate statistics to be performed, so standard protocols (such as feedback forms) and other techniques should be used.

Periodically, these guidelines and policies can be changed following researcher feedback. In particular, FIPs can be re-evaluated for relevance and fitness of purpose.

## Roles and responsibilities
In this piece, I talk at length about Data Stewards but never define their role in detail.
I hope that the reader could have picked up the outline of Data Stewards in my conceptualization of the research process.
In any case, I explicitly explain it here. As sources, I use the work of the FAIRsFAIR competence framework for data stewards (my notes can be found [here](https://mrhedmad.github.io/data-stewardship-knowledgebase/competences.html)), and the Data Stewards: Minimum Viable Skills Profile report from the Skills4EOSC consortium (available on Zenodo [in short form here](https://zenodo.org/records/14006764) and [in long form here](https://zenodo.org/records/8101903)).

A Data Steward (DS for short) is a professional figure with expertise in the handling of data, with a multifaceted skillset. A Data Steward's primary mission is to preserve data for later reuse, be it for the benefit of an organization, a sovereign state or the whole community.

First, as modern data is overwhelmingly digitized, a DS has technical knowledge of the strategies to harvest, store, manipulate and preserve digital data. This includes the creation of data-processing pipelines (e.g. for [data ingestion](https://en.wikipedia.org/wiki/Data_preparation)), the design and administration (but potentially not the maintenance) of data archives and repositories, and the day-to-day handling of edge cases encountered during data management. Concrete skills include programming, knowledge of data formats and computer systems, concepts of data and systems security, and more.
While a DS's day-to-day may not involve significant [data wrangling](https://en.wikipedia.org/wiki/Data_wrangling) or otherwise data handling *per se*, DSs must understand what these processes involve, as they both define the boundary of what is possible to do with data, and how data is ultimately used by the data (re)users.

Additionally, as software can be, in a way, seen as *data that can be executed*, knowledge in the preservation of software for later execution is important.

Secondly, to unlock the data for reuse, the fine conceptualization of what the data is describing and the epistemic need that it is trying to fulfill need to be understood, made explicit, and preserved. For this reason, a Data Steward has factual knowledge and expertise in specific application domains (read: Arts, Biology, Earth Sciences, Medicine, etc...), as well as familiarity with those ways in which the reusable data they strive to create will be used, in order to meet the demands of their fields and organizations. Additionally, as ontologies and supra-ontological frameworks are routinely used to address these concerns, knowledge of the creation and usage of these systems is fundamental for any Data Steward.

Thirdly, soft skills such as communication, mediation, leadership capacity, ability to work and coordinate large teams, and engagement, as well as hard skills such as data privacy, ethical knowledge and the ability to draft and put in application policies regarding data are extremely useful for Data Stewards. Indeed, there is a significant need for professionals who both have the domain and technical knowledge to guide the whole data lifecycle, with its multifaceted aspects (see [here](https://rdm.unimi.it/research-data-lifecycle/) and [here](https://privsec.harvard.edu/data-lifecycle) for more on the data lifecycle). Given the centrality of this role, soft communication skills as well as robust core abilities and expertise to deal with the many issues which arise when several varied stakeholders collide (researchers/data creators, data (re)users, organizations, laws, legal entities, states and the whole community) is of enormous importance.

Finally, and more relevant for those Data Stewards in academia and generally working for the benefit of the community, Data Stewards are trained in the principles, philosophy and methods of Open Science.
In this context, Open Science is understood as that practice that aims to render public research more useful for the public, in particular by being more trustworthy, accessible, and aligned with human and societal needs.
According to this framework, Data Stewards are both enablers and teachers of Open Science, in many different contexts.
For this point, the raw knowledge of the history, practice and philosophy of Open Science is fundamental, as well as other soft skills such as community engagement, lecturing and divulgation.

## FAIR Implementation Profiles
As the keen reader will have undoubtedly noticed, I've delegated many important and hard tasks to the FAIR Implementation Profiles (FIPs). Here I attempt to delineate these issues, providing my idea of what FIPs are and some of the characteristics that they require in the context of Open Research. While the confrontation of these issues is relegated to a later date and open to debate (it is an open question in the above text), here I hope to bind this conversation to more defined areas.

As a summary and basis for this section, I list here all the aspects of Open Research that depend on the FIPs:
- The specific data creation protocols and data types that the FIP applies to;
- The raw format of the data created by the data collection process (e.g. the machine that does the measurement);
- How this raw data is stored;
- How the raw data is preprocessed to create experiment-level data packages, containing all the data of the same type created by the specific experiment;
- The required metadata, characteristics and formats that the data has to have to create an archival package, including which ontologies will be used to explicitly define the semantics of the data, and all other aspects needed to make the data FAIR;
- The archival strategies that the archival packages are subjected to, including defining which repository to use.

Potentially more aspects should be covered by the FIPs, but they are yet unclear to me. In any case, the burden placed on the FIPs is enormous. However, this key role of FIPs makes them ideal candidates as facilitators of data handling. Executable FIPs, whereas an infrastructure may be able to guide the primary data generators through the process of creating, storing, preprocessing, annotating with metadata, and ultimately depositing the data can be envisioned.

Of course, the task of creating such a FIP for all the potential data types is enormous, and potentially infinite. However, such strategies can be reused over time, slowly eroding the problem of non-reusable data.

FIPs are not to be intended as prescriptive. In no way does the presence (or more importantly the absence) of a FIP have any influence on the freedom of experimentation that every researcher has. It is not the job of FIPs - or Data Stewards for that matter - to legislate what can and cannot be done with data. Their only role - and I cannot stress this enough - is to support the proper handling of data for the benefit of the researchers themselves and crucially for future data (re)users.

## Benefits of Open Research
This research framework has several inherent benefits. I detail some of them here.
### For Researchers
- It allows increased focus on the research problems at hand, and predicts potential pitfalls during the experimental process;
- When the experimental phase starts, Structured protocols significantly ease its execution.
- Careful consideration of every experiment's planning and outcomes limits wasted resources, especially in terms of time.
- Centralized places to store and structure all outcomes of experiments reduce confusion and limit the possibility of accidentally losing data;
- The creation of the project plan can align all contributors to the project on its goals, expected outcomes and procedures.
- For projects with many experimenters, the project plan can help to subdivide work into packages more effectively and distribute these to different people/groups/organizations.
- Routinely creating high-quality project plans, even for master students, can help when eventually dealing with funding agencies.
- Structured protocols and specifically the creation of interpretations can ease the creation of high-quality manuscripts.
- The creation of nanopublications increases the reach and visibility of one's own research.
- More granular and insightful consideration of the knowledge derived from each experiment can promote increased awareness of one's own work.
- Predetermined data handling and analysis procedures can reduce potential errors, such as data loss or the application of inopportune statistical tools.

### For the community
- FAIR data enables interoperability and FAIR orchestration services to be built on top of it.
- The repository of curated FIPs and Structured protocols can be reused by the community to increase the quality and FAIRness of their own data;
- Transparency in the experimental process can allow faster review of the material;
- Pre-registering studies allow for collaborations to form between members of the community;
- FAIR data reuse limits wasteful experimentation.
- The FAIR data limits the difficulty of data munging.
- Availability of negative results together with positive ones enables more insight when running large-scale meta-analyses.

### For institutions and funding agencies
- Keeping track of the number of projects created and followed through can be used as a quality metric;
- The ever-increasing body of FAIR data can be a strong political asset when dealing with funding agencies and international consortia;
- Granular statistics on the *actual* scientific production (number, type, scope of data gathering or processing) of every member of the institution can be derived from the metadata, enabling greater insight into the organization itself;
- The intervention of external data stewards can limit the possibility of scientific fraud, and the resulting social, political and financial downsides for the institution;

### For society
- Citizens can access the knowledge that they funded, transparently;
- Citizen scientists can tap into data that they could not otherwise produce on their own;
- A transparent research process can increase societal trust in science, especially in times of crisis.
- Governments can access the available data to inform political action, e.g. in the public health or environmental sciences.
