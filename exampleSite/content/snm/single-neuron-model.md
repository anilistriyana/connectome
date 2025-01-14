---
title: Single Neuron Models
date: 2016-03-18 00:00:00 Z
layout: notes
authors:
- ErbB4
summary: Neuron biological properties
type: project
links:
- snm/limitations-srm-contd-and-coding.md
- snm/single-neuron-model.md
weight: 2
---

## Neuron biological properties

Dendrites receive neurotransmitter and generate local post-synaptic potential (PSP), either excitatory by glutamate or inhibitory by GABA. Soma integrates all PSPs. Once membrane potential reaches the threshold, an action potential is generated. Action potentials are propagated via axon.

### Spike Response Model (SRM)

In this model, membrane potential is denoted as u(t). When the neuron is at rest state, receiving no external stimulation, the membrane potential is called rest potential.


$$u(t_0)=u_{\mathrm{rest}}.$$


When a presynaptic spike arrives, there is a local PSP, causing a small disturbance in membrane potential.

$$u(t)-u_{\mathrm{rest}} = e_{ij}.$$

Throughout the notes, $i$ is always indicating the neuron we are measuring the potential, while $j$ is for the incoming signal.

According to simplification rule, all PSPs are integrated linearly.

$$u_i(t) =u_{\mathrm{rest}}+ \sum_{j} \sum_f \epsilon_{ij}(t - t_j^{(f)}) $$

in which $(f)$ shows the $j$ neurons can fire multiple times.

However, when an action potential is generated, there is a dramatic membrane potential change (depolarization), and due to the electrophysiological property of channels, hyperpolarization phenomenon is observed. So the complete but simple presentation of membrane potential is

$$u_i(t) =u_{\mathrm{rest}}+ \sum_{j} \sum_f \epsilon_{ij}(t - t_j^{(f)}) + \eta(t-\hat t_i),$$

where $\hat t_i$ is the moment when the action potential is triggered.



### Spike train

When simulating a neural network, we don't care about the exact trajectory of membrane potential.
so Dirac function is used to present an action potential. This provides the first step to computation, using firing times to present the spike train of a neuron.

### Limitation of SRM

SRM cares about merely the most recent spike, however in real case, previous spikes could influence the reaction of the neuron to a later simulation. (for example, by changing membrane conductivity)
