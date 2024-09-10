# Power Platform CLI

1. Visual Code Plugin

https://learn.microsoft.com/de-de/power-platform/developer/cli/introduction

1.1. Commands

https://learn.microsoft.com/de-de/power-platform/developer/cli/reference/

Command Group

Description

pac admin

Work with your Power Platform Admin Account

pac application

Commands for listing and installing available Dataverse applications from AppSource

pac auth

Manage how you authenticate to various services

pac canvas

Operating with Power Apps .msapp files

pac catalog

(Preview) Commands for working with Catalog in Power Platform

pac connection

(Preview) Commands for working with Dataverse connection.

pac connector

(Preview) Commands for working with Power Platform Connectors

pac copilot

Tools and utilities for copilot scenarios

pac data

Import and export data from Dataverse.

pac help

Show help for the Microsoft Power Platform CLI.

pac modelbuilder

Code Generator for Dataverse APIs and Tables

pac org

Work with your Dataverse organization.

pac package

Commands for working with Dataverse package projects

pac pcf

Commands for working with Power Apps component framework projects

pac pipeline

Work with Pipelines

pac plugin

Commands for working with Dataverse plug-in class library

pac powerpages

Commands for working with Power Pages website.

pac solution

Commands for working with Dataverse solution projects

pac telemetry

Manage telemetry settings.

pac test

(Preview) Execution of automated tests for a Power App

pac tool

Power Platform tools that can be installed and launched.

pac virtual-agent

Commands for working with Power Virtual Agent bots

1.1.1. Examples

Just hit the ground with PoSh or Shell (zsh) – following examples make use of PoSh:

# Authenticate
pac auth list
pac auth select --index 3

##########################
# Select environment
# pac org [who] [list] [fetch] [list-settings] [update-settings] [select]
pac org list
# Usage: pac org select --environment (alias: -env)
pac org select -env "https://tmaestrini-test.crm17.dynamics.com"

##########################
# Work with solutions
pac solution help

# Usage: pac solution list [--environment]
pac solution list
# Usage: pac solution export --name [--path] [--managed] [--include] [--async] [--max-async-wait-time] [--overwrite] [--targetversion]
pac solution export 


##########################
# Administer the environment
pac admin help

# Usage: pac admin create [--name] [--region] --type [--currency] [--language] [--templates] [--domain] [--input-file] [--async] [--team-id] [--max-async-wait-time]
pac admin create 

1.2. Create Build and Release Tasks

1.2.1. Build Tasks

##########################
# Authenticate
pac auth list
pac auth select --index 2
pac org select -env "https://metaconstruction.crm17.dynamics.com" # development environment

##########################
# Get the solution and unpack the artifacts
pac solution list
pac solution export --path ./Bauprojekte.zip --name Bauprojekte --include general,customization
pac solution unpack --zipfile ./Bauprojekte.zip --folder ./Bauprojekte

##########################
# Update the solution on PPL and build a deployable managed solution
pac solution pack --zipfile ./Bauprojekte_managed.zip --folder ./Bauprojekte --packageType Unmanaged --processCanvasApps
pac solution import --path ./Bauprojekte_managed.zip
pac solution export --name Bauprojekte --path ./Bauprojekte_managed.zip --managed # uses the PPL JIT Compiler to build a managed solution

1.2.2. Release Tasks

# Authenticate
pac auth list
pac auth select --index 2
pac org select -env "https://metaconstruction.crm17.dynamics.com" # production environment

##########################
pac solution import --path ./Bauprojekte_managed.zip

