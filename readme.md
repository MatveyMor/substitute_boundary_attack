# Surrogate models help black box adversarial attacks
## Machine Learning 2021 Course by E. Burnaev, A. Zaytsev et al., Skoltech

Team members: Matvey Morozov, Anna Klueva, Elizaveta Kovtun, Dmitrii Korzh

### Introduction

Adversarial attack is a way to exploit the non-robustness of deep learning modes, it means that slight modifications of the input may lead to the inability of the model to get the correct answer. In this project, we consider a modification of boundary black-box adversarial attacks on deep neural networks for image classification problem. In the process of generating examples for an attack, we use an additional step based on a surrogate model for the attacked model.

Our implementation for Substitute Boundary Attack is based on FoolBox framework implemenation https://foolbox.readthedocs.io/en/stable/index.html

Example of attack running:

```
fmodel = foolbox.PyTorchModel(model, bounds=(0, 1), device=device)

attack = BoundaryAttack(steps=25000, tensorboard='./logs')

adversarial = attack(model=fmodel, 
                     inputs=input_or_adv, 
                     starting_points=starting_points, 
                     criterion=fb.criteria.Misclassification(label), 
                     epsilons=1e-3)
```
where `fmodel` -- foolbox PyTorch model to be attacked, `input_or_adv` -- image to be perturbuted, `starting_points` -- starting adversarial examples, images from another class.
 
More examples of experiments running you can find in the `experiments` directory.
 
