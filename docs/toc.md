<!-- toc-page -->
<style>
  /* Hide the ToC on its own standalone site page (screen), but keep it
     visible inside the combined print page (#print-site-page) so it can
     render into the PDF. Never touches .md-main__inner or the site chrome. */
  @media screen {
    .toc-page { display: none; }
    #print-site-page .toc-page { display: block; }
  }
  /* Keep the ToC's own group headers flowing on one page in print,
     without re-paginating h2 headings anywhere else in the document. */
  @media print {
    .toc-page h2 { page-break-before: auto !important; }
  }
</style>

<div class="toc-page" markdown>

# **Table of Contents**

## [Introduction](index.md)

- [1. IBM i modernization is indispensable to enterprise IT](index.md#i-ibm-i-modernization-is-indispensable-to-enterprise-it)
- [2. What is IBM Bob?](index.md#ii-what-is-ibm-bob)
- [3. What the Premium Package for i adds](index.md#iii-what-the-premium-package-for-i-adds)
- [4. The environment: the FLIGHT400 application](index.md#iv-the-environment-the-flight400-application)
- [5. Lab objectives](index.md#v-lab-objectives)
- [6. Lab prerequisites](index.md#vi-lab-prerequisites)
- [7. Next steps](index.md#vii-next-steps)

## [Registration and Setup](setup.md)

- [1. Before you begin](setup.md#i-before-you-begin)
- [2. Request entitlements to Bob Premium Package for i](setup.md#ii-request-entitlements-to-bob-premium-package-for-i)
- [3. Install and authorize Bob Premium Package for i](setup.md#iii-install-and-authorize-bob-premium-package-for-i)
- [4. Install the IBM i Development Pack](setup.md#iv-install-the-ibm-i-development-pack)
- [5. Reserve the IBM i 7.6 virtual machine](setup.md#v-reserve-the-ibm-i-76-virtual-machine)
- [6. Download the lab assets](setup.md#vi-download-the-lab-assets)
- [7. Set up the Project workspace](setup.md#vii-set-up-the-project-workspace)
- [8. Connect to the IBM i LPAR](setup.md#viii-connect-to-the-ibm-i-lpar)
- [9. Enable the 5250 terminal](setup.md#ix-enable-the-5250-terminal)
- [10. Uploading the Flight400 files to the IFS](setup.md#x-uploading-the-flight400-files-to-the-ifs)
- [11. Restoring the FLGHT400 library](setup.md#xi-restoring-the-flght400-library)
- [12. Adding FLGHT400 to your library list](setup.md#xii-adding-flght400-to-your-library-list)
- [13. You're ready to proceed](setup.md#xiii-youre-ready-to-proceed)

## [Analyze - Legacy IBM i to Living Documentation](1-1.md)

- [1. Where modernization begins](1-1.md#i-where-modernization-begins)
- [2. Why this matters](1-1.md#ii-why-this-matters)
- [3. Analyzing FLIGHT400 with IBM Bob](1-1.md#iii-analyzing-flight400-with-ibm-bob)
- [4. Setting up the object browser](1-1.md#iv-setting-up-the-object-browser)
- [5. Initializing Bob's context with /init](1-1.md#v-initializing-bobs-context-with-init)
- [6. Scanning the application with the Understand Dashboard](1-1.md#vi-scanning-the-application-with-the-understand-dashboard)
- [7. Extracting business rules from an RPG program](1-1.md#vii-extracting-business-rules-from-an-rpg-program)
- [8. Generating an architecture overview](1-1.md#viii-generating-an-architecture-overview)
- [9. Adding an entity relationship diagram](1-1.md#ix-adding-an-entity-relationship-diagram)
- [10. Key takeaways](1-1.md#x-key-takeaways)

## [Modernize - Modernizing OPM RPG to Free-Format ILE](2-1.md)

- [1. From understanding to transformation](2-1.md#i-from-understanding-to-transformation)
- [2. Why this matters](2-1.md#ii-why-this-matters)
- [3. Modernizing FRS409 with IBM Bob](2-1.md#iii-modernizing-frs409-with-ibm-bob)
- [4. Understanding FRS409](2-1.md#iv-understanding-frs409)
- [5. Running the RPG modernization workflow](2-1.md#v-running-the-rpg-modernization-workflow)
- [6. Key takeaways](2-1.md#vi-key-takeaways)

## [Modernize - Extending Business Logic Across the Stack](2-2.md)

- [1. From single-program modernization to cross-stack change](2-2.md#i-from-single-program-modernization-to-cross-stack-change)
- [2. Why this matters](2-2.md#ii-why-this-matters)
- [3. Extending Total Flight Hours with IBM Bob](2-2.md#iii-extending-total-flight-hours-with-ibm-bob)
- [4. Creating standing rules for IBM i Developer mode](2-2.md#iv-creating-standing-rules-for-ibm-i-developer-mode)
- [5. Exploring the flight maintenance screen](2-2.md#v-exploring-the-flight-maintenance-screen)
- [6. Performing a focused impact analysis](2-2.md#vi-performing-a-focused-impact-analysis)
- [7. Updating the DDS source](2-2.md#vii-updating-the-dds-source)
- [8. Updating the display file](2-2.md#viii-updating-the-display-file)
- [9. Updating the RPG program](2-2.md#ix-updating-the-rpg-program)
- [10. Compiling all four objects](2-2.md#x-compiling-all-four-objects)
- [11. Validating the end-to-end field mapping](2-2.md#xi-validating-the-end-to-end-field-mapping)
- [12. Testing on a live 5250 terminal](2-2.md#xii-testing-on-a-live-5250-terminal)
- [13. Key takeaways](2-2.md#xiii-key-takeaways)

## [Optimize - Reviewing and Tuning Db2 for i SQL](3-1.md)

- [1. From source code to the database beneath it](3-1.md#i-from-source-code-to-the-database-beneath-it)
- [2. Why this matters](3-1.md#ii-why-this-matters)
- [3. Optimizing FLIGHT400 queries with IBM Bob](3-1.md#iii-optimizing-flight400-queries-with-ibm-bob)
- [4. Reviewing a query with /review](3-1.md#iv-reviewing-a-query-with-review)
- [5. Running the SQL Index Strategy Advisor workflow](3-1.md#v-running-the-sql-index-strategy-advisor-workflow)
- [6. Key takeaways](3-1.md#vi-key-takeaways)

## [Test - Planning and Implementing RPGUnit Tests](4-1.md)

- [1. From a tuned database to a tested codebase](4-1.md#i-from-a-tuned-database-to-a-tested-codebase)
- [2. Why this matters](4-1.md#ii-why-this-matters)
- [3. Testing FLIGHT400 with IBM Bob](4-1.md#iii-testing-flight400-with-ibm-bob)
- [4. Installing RPGUnit on the partition](4-1.md#iv-installing-rpgunit-on-the-partition)
- [5. Creating the CUSTCHK source member](4-1.md#v-creating-the-custchk-source-member)
- [6. Running the RPGUnit Test Plan Creation workflow](4-1.md#vi-running-the-rpgunit-test-plan-creation-workflow)
- [7. Running the RPGUnit Test Suite Implementation workflow](4-1.md#vii-running-the-rpgunit-test-suite-implementation-workflow)
- [8. Key takeaways](4-1.md#viii-key-takeaways)

## [Operate - Operating IBM i with Natural Language](5-1.md)

- [1. From modernization to operations](5-1.md#i-from-modernization-to-operations)
- [2. Why this matters](5-1.md#ii-why-this-matters)
- [3. Querying your IBM i with Bob](5-1.md#iii-querying-your-ibm-i-with-bob)
- [4. Key takeaways](5-1.md#iv-key-takeaways)
- [5. Earn accreditation](5-1.md#v-earn-accreditation)
- [6. Congratulations](5-1.md#vi-congratulations)

## [Extend (optional) - Generating a React Carbon App from a Green Screen](6-1.md)

- [1. From the green screen to the browser](6-1.md#i-from-the-green-screen-to-the-browser)
- [2. Why this matters](6-1.md#ii-why-this-matters)
- [3. Extending FLIGHT400 with IBM Bob](6-1.md#iii-extending-flight400-with-ibm-bob)
- [4. Preparing Node.js on the partition](6-1.md#iv-preparing-nodejs-on-the-partition)
- [5. Creating the helper skill](6-1.md#v-creating-the-helper-skill)
- [6. Generating the React application](6-1.md#vi-generating-the-react-application)
- [7. Opening the application from your laptop](6-1.md#vii-opening-the-application-from-your-laptop)
- [8. Key takeaways](6-1.md#viii-key-takeaways)

</div>
