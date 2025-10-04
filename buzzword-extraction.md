```
It takes a block of text and identifies every clearly named software, technology, or methodology term that qualifies as a technical “buzzword.”

For each buzzword, it:
	1.	Extracts explicitly mentioned terms only - no guessing or adding related concepts.
	2.	Preserves full names and acronyms - keeps product and framework names intact.
	3.	Skips overly generic words unless part of a specific named concept.
	4.	Organizes results by category such as AI/ML, Cloud Services, Frameworks, or Methodologies.
	5.	Groups related tools by company or family under clean markdown headers for easy reading.

The result is a structured, resume-ready list of categorized buzzwords.
```

<instructions>
	Extract all software, technology, and methodology buzzwords from the provided text wrapped in <text> tags. A "buzzword" is any term that represents a specific named technology, tool, methodology, or technical concept that would appear on a resume or technical skills list.

	<extraction_instructions>
		<extraction_rules>
			1. Extract only explicitly mentioned terms - Do not infer, generalize, or add related terms that aren't directly stated in the text.
			2. Keep proper nouns intact - Never split proper nouns.
			3. Preserve full product names - Extract complete product names as written (full name unless the shortened version appears standalone).
			4. Handle variants separately - When a base product and its variant/version both appear, list both.
			5. Use plural forms - When singular and plural forms both appear, use only the plural.
			6. Include ambiguous terms - Extract terms even if they could be practices, concepts, or functions.
			7. Extract acronyms with full forms - Include both when present.
			8. Avoid overly generic terms - Skip standalone terms like "IT", "AI", "cloud", "technology", "software", "data" unless they're part of a specific named concept. However, DO include qualified/specific types (e.g., "conversational analytics", "predictive analytics", "behavioral analytics").
		</extraction_rules>
		
		<what_is_a_buzzword>
			A term qualifies if it is:
			- A specific named product, service, or platform (identifiable by capitalization or context)
			- A programming language
			- A framework, library, or SDK
			- A methodology or process framework (named approaches to work)
			- A technical concept or architecture pattern (that would be listed as a skill)
			- A tool or application used in technical work
			- A certification, standard, or protocol name
			- An acronym representing a technical concept with its full form if provided
			- A specific product/project management practice, technique, or deliverable (e.g., "roadmap creation", "sprint planning", "backlog management")
		</what_is_a_buzzword>
		
		<organization>
			Organize extracted terms into logical categories based on their technical nature.
			
			Common categories include:
			- AI/ML Technologies
			- Cloud Services
			- Development Tools & Platforms
			- Frameworks & Libraries
			- Databases
			- ITSM & Service Management
			- Programming Languages
			- Methodologies
			- Product/Project Management
			- Other Technologies
			
			Create new categories as needed for terms that don't fit the above.
			
			Within each category, group related products by their parent company or product family. Use sub-bullets only for products within the same company/family. Keep standalone products at the top bullet level within their category.
		</organization>
	</extraction_instructions>

	<response_format>
		Use markdown format with the following structure:
		## Category Name
		- **Company/Product Family** (when multiple related products exist)
		  - Sub-product 1
		  - Sub-product 2
		  - Sub-product 3
		- Standalone Product (when no related products in this category)
		- Another Standalone Term
		
		<example>
			## Development Tools & Platforms
			- **Microsoft**
			  - Microsoft CoPilot
			  - Microsoft CoPilot Studio
			  - Power Platform
			  - Power Automate
			  - Power Apps
			  - Power BI
			  - Power Virtual Agents
			
			## Cloud Services
			- Azure Bot Services
			
			## ITSM & Service Management
			- **Atlassian**
			  - Jira Service Desk
			- IT Service Management (ITSM)
			
			## Methodologies
			- Agile
			- Scrum
			- Kanban
		</example>
		
		Do not include any introductory text, explanatory text, or commentary. Only output the categorized list with company groupings as shown above.
	</response_format>
</instructions>

---

<text>
{text}
</text>

---

Extracted Buzzwords:
